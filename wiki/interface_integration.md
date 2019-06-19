
# Interface integration

_Matt, Dmitry D., Geoff, Jonathan_

## Goal

Our goal was to integrate 3 resources (gnfinder, gnparser, and the BHL API) into a 4th, TaxonWorks.  

## Initial brainstorming

TODO: link images
* [ ]()

### Use case 0 - Determine if there is a reasonably probable resolution of some Source in TaxonWorks to a "resource" in BHL 

This is the same as adding a method `@source.found_in_bhl?` to TaxonWorks. The result likely has to be fuzzy, because the BHL doesn't track individual references, and there are multiple possible links between serials, etc. possible. I.e. there is some fuzzy/interpretation of the results required to get from points A to B thanks to issues with linking metadata.

Other methods of need are along the line of `@source.bhl_image_for_page?(22)` and `@source.bhl_ocr_for_page?(22)`.

### Use case 1 - Show page (image) of original description from BHL given only Source/Citation in TaxonWorks

```
From TaxonWorks Task:
BHL API call 1:
PublicationSearchAdvanced
Title (journal title matching)
https://www.biodiversitylibrary.org/api2/httpquery.ashx?op=GetTitleMetadata&titleid=9426&items=t&apikey=<key+value>
titleid - is a Serial id, the api will return the list of items with the ids
BHL API call 2: 
GetTitleMetadata
https://www.biodiversitylibrary.org/api2/httpquery.ashx?op=GetItemPages&itemid=38713&ocr=f&apikey=<key+value>
itemid - is a volume id, the api will return the list of pages with the ids
BHL API call 3:
Working on this step
Step three: get an url for an individual page and display it. There are also urls for thumbnails, so we can display the current page as well as thumbnails for the previous and the next pages.
```

### Use case 2 - Given taxon name from TaxonWork find all "references" to this name in the BHL and summarize them in display

## Overall outcomes

* Updated [rubyBHL](https://github.com/SpeciesFileGroup/rubyBHL) to match the BHL's v3 API
* Added gnparser and gnfinder gems, with simple specs, to TaxonWorks 
* Mocked a landing place (== "Task" in TaxonWorks to experiment with the 3 API wrappers) - [TaxonWorks Commit](https://github.com/SpeciesFileGroup/taxonworks/commit/9f1c0af92a456cff1baaa0ad60ade9b776849bae)
* Ran some BHL queries in the Task.
* Parsed and proofed `title.txt` finding errors in the CSV that can be resolved by BHL
* Discussed the route that traverses metadata from TW serials to BHL metadata.  There are various issues with multiple records in BHL, and how they store data that lead to it being difficult to go 1:1 from Source to pages. Final traversal will have to a be "fuzzy" method in TaxonWorks, or elsewhere.
 
