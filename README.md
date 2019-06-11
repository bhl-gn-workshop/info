# BHL/GN workshop 2019 cheatsheet

- [BHL/GN workshop 2019 cheatsheet](#bhlgn-workshop-2019-cheatsheet)
  - [General Information](#general-information)
  - [BHL Data and Metadata Mobilization](#bhl-data-and-metadata-mobilization)
    - [BHL Metadata Download](#bhl-metadata-download)
    - [BHL API](#bhl-api)
    - [BHL Text Data Download](#bhl-text-data-download)
  - [Global Names Lexical Tooling](#global-names-lexical-tooling)
    - [gnfinder](#gnfinder)
    - [gnindex](#gnindex)
    - [gnparser](#gnparser)
    - [bhlindex](#bhlindex)

## General Information

See the [workshop web page](https://globalnames.org/workshops) for logistics.

Our workshop is about leveraging resources of Biodiversity Heritage Library and lexical tools of Global Names project to work on BHL texts for data-mining and improving quality of its metadata.

We hope to figure out how to mobilize BHL data and meta-data better and to improve quality of scientific names finding in its corpus.

## BHL Data and Metadata Mobilization

Before we can do work on the whole corpus of BHL data and metadata we need to get this data on our local computer. Here are resources that can help with the process.

### BHL Metadata Download

BHL provides its metadata under CC0 1.0 Universal license. Whole content of
BHL metadata database can [be downloaded](https://about.biodiversitylibrary.org/tools-and-services/developer-and-data-tools/) for local use.

### BHL API

[BHL API](https://about.biodiversitylibrary.org/tools-and-services/developer-and-data-tools/#APIs) allows to get data that is too big, or too cumbersome to get in bulk, like for example, original scans of the pages.

### BHL Text Data Download

Currently there is no "official" way to download all textual data of BHL. However it is crucial to have this data available for remote researches who work on data-mining projects in BHL. We are planning to look at several possible ways to get the entirety of textual data from BHL, as well as fast mobilization of data for selected titles.

We tried several different approaches so far. We tried to use rsync to move files containing BHL texts. However we found this approach proved to be very slow -- it took us 10 days to move 54 million files from Smithsonian to University of Illinois.

Jorrit Poelen and Dima Mozzherin tried using standard archival tools as well. Creation of gzipped tar archive took about 2-3 hours. Subsequent downloading of the [file](http://opendata.globalnames.org/dumps/) using http protocol using lftp tool took approximately 5 hours. It was also possible to continue download if download was interrupted by some reason.

We tried to use gRPC framework that can create one- or two-directional streams of compressed data to a client. On a fast network we were able to transfer scientific name occurences metadata together with 54 million pages of text in 3 hours using fast network, and in 20 hours using slower WiFI network.
An experimental gRPC service is located at [http://bhlrpc.globlanames.org](http://bhlrpc.globlanames.org) and can be tried by using a crossplatorm gRPC B HL client [bhlclone](https://github.com/gnames/bhlclone/releases/tag/v0.0.1). You can download the tool binary according to your operating sytem, move it
somwhere in your path. Then run

    bhlclone help

To get help. To get pages out of the first 10000 BHL volumes with names occurences and texts

    time bhlclone pages -s 1 -e 10000 -t

## Global Names Lexical Tooling

Global Names lexical tools sit before taxonomic or nomenclaural usages of scientific names. These tools can detect scientific names in texts, reconcile lexical variants of names, and resolve such names against a variety of biodiversity data sources.

### gnfinder

The [gnfinder](https://github.com/gnames/gnfinder) tool uses heuristic and Bayes approaches to pick scientific names with and without OCR errors out of UTF-8 encoded texts. This tool can be used as a library and as a command line application. For example to find names and then verify them against NCBI and Encyclopedia of Life (data source IDs 4 and 12 correspondingly) using setting English as the language for a document redirecting JSON results to a file:

    gnfinder find file1.txt -c -l eng -s "4,12" > file2.json

Its functionality is also exposed as gRPC service. An example client for the service is presented as a [gnfinder Ruby gem](https://gnrd.globalnames.org/:w
)

There is also [gnrd](https://gnrd.globalnames.org/) web-application that allows to find names in a variety of formats -- MS World documednts, spreadsheets,
PDFs, images, plain texts.

### gnindex

A [web-wervice](https://bit.ly/2AZJngf) that uses GraphQL API to resolve incoming names against a large variety of datasets. This service is used by gnfinder for name reconciliation and resolution

### gnparser

The [gnparser tool](https://parser.globalnames.org/) is a library that breaks scientific name-strings into semantic elements of the string. It is extremely efficient and precise library very important for reconciliation of various spellings of scientific names.

### bhlindex

The [bhlindex](https://github.com/gnames/bhlindex) project uses all tools mentioned above to find and verity scientific names in Biodiversity Heritage Library.

The tool currently also includes a service that is able to create a gRPC stream of BHL data and name occurences to a remote user. An experimental stream currently resides at [http://bhlrpc.globalnames.org](http://bhlrpc.globalnames.org).