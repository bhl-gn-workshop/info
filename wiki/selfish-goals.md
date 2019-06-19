# Selfish Goals

Some participants of the workshop defined goals their organizations/projects
would like to achieve as a result of the workshop.

## Global Names

1. Create solid workflow for name indexing (total and incremental)
2. Figure out solid workflow for fast mobilization of BHL data and metadata
3. Have a better understanding what missing BHL metadata would be most useful,
  and how to acquire it
4. Collect data/ideas for a successful grant about improving BHL metadata and
  name index

## TaxonWorks

1. Define “Epic” style tasks that integrate BHL+GN and TW functionality.
  With well defined use/competency cases.
2. Enable name-finding for users of TaxonWorks, so they can extract names
  mentioned in their resources.
3. Link BHL resources as TW subclasses (e.g. pages as Images) so that they
  can be further parsed with GN tools, or use do to depict metadata.
4. Use BHL/Global Names to create “bare bones” new catalog for COL missing
  groups (example “Epic Task”) that integrates BHL references/metadata and
  COL/Global Names names

## Catalogue of Life

1. Connect CoL species with original publications of species descriptions in BHL
2. Extracting species data from BHL (e.g., distribution)

## BHL

1. Specimen Identification in BHL Text - Link a Specimen ID back to the item
  in its source collection
2. Identify TraitBank attributes in BHL Text
3. Find original identification/publication in BHL to connect to Catalogue of
  Life (similar to Index Animalium, related to Tropicos?)
4. Define how to report errors in names to GN.
5. Define a data flow for corrections to names in GN and round-trip those
  changes back into BHL and others?
6. (something related to treatments TBD)
7. Move metadata around expert-sourced “identified parts” within BHL to
  places like TaxonWorks, COL (similar to #3, #1 in COL)

## DINA

1. Identify candidate associations among names based on proximity on the page,
  supplement with search for known phrases that may indicate nature of
  association (eg predator of, prey of, etc.)
2. Explore other entity extraction libraries or services
  (eg Rosette, https://www.rosette.com/) for people, places, dates, lat/long,
  traits, other & tie to URIs like wikidata QIDs
3. User interface to overlay & highlight extracted names on BHL page as a
  precursor to BHL #4, #5 above & general annotation UI.
  See https://github.com/dshorthouse/ocr-correction based on DjVu files from
  an earlier hackathon in Leiden

## EOL

1. BHL links on EOL taxon pages: Tools to facilitate mapping of taxon names to
  EOL pages (homonyms, unknown synonyms).
2. Tools to sort/filter links by date of publication, relevance (e.g.,
  occurrence of name in item, occurrence of name in headers), item properties
  (subjects, item types), context properties (nomenclatural acts,
  identification keys, illustrations, checklists, etc.). Snippet views of
  content associated with a link.
3. Text mining for structured data: Semantic extraction/annotation of
  candidates for TraitBank attributes & values, persons & institutions,
  geographical entities, putative biotic interactions. Identification of
  sub-corpora suitable for structured data mining.
4. BHL taxonomy statistics. Compare to EOL coverage/treatment of names
  (overlap, taxonomic status, mapped to reference hierarchy, sources of
  missing, unmapped names, characterize EOL names not covered by BHL).
  Assess/visualize BHL coverage/gaps.


## iDigBio (DP)

1. RE: BHL #1 above, figure out how to link BHL records to relevant specimen
   records currently published in iDigBio. How do we figure these out? We
   could send this information back to data providers, so they can add these
   URLs and BHL IDs to their own database specimen records.
2. RE: DINA #1,2,3. Ideas for how to create a visual (from OCR) search, using
   something analogous to carrot-squared. (People, Places, Names, Traits).
   See screen shots.
3. Could use ENVO, PPO, other ontologies to work on DINA #1. Trait Data
   Extraction and visualization. (See screen shots).
4. Potential to add BHL to ePANDDA API
5. Linking BHL records with Bloodhound-tracker.net
6. Artists - how do we increase awareness, linking, and findability of
   art in BHL?

## Global Biotic Interactions and more (Jorrit)

Taxonomic names (warts and all) have been the (subjective) semantic glue that
has integrated biodiversity data over the last centuries.

Today, names remain important. Empowered by falling costs of digital storage,
bandwidth and compute power and the proliferation of open datasets, various
projects have started to break down traditional siloes by establishing
granular links and create engaging user interfaces to enjoy them. However,
evidence suggests that these links break (e.g., linkrot, bit rot), linked
content changes (e.g., taxonomic name changes, content drift, invalid links)
and little is known about the quality of these links. (If you need specific
examples, please contact Jorrit).

We need clearly defined, stable, and reproducible, linking processes to help
build a consistent digital record based on ground truths. Note that
controlled linked processes are not just a benefit to a consistent scholarly
record: development of tools (e.g., gnfinder, gnparser,
https://github.com/bio-guoda/preston,
https://github.com/globalbioticinteractions/nomer,
https://github.com/globalbioticinteractions/elton,
https://github.com/cboettig/taxadb) used in projects like Globalnames, GloBI,
ropensci have gravitated to help support these reproducible, offline-enabled
processes simply because of pragmatic reasons (e.g., scalability,
performance, dealing with in-stable APIs, keeping costs down by building
modular, maintainable workflows that can be easily replayed and fixed).

This leads me to propose the following goals:

1. document how existing (name) links are currently maintained  across the
   various projects (e.g., gn, eol, col+, gbif, idigbio, globi)
2. reach consensus and propose (or re-use) a conceptual model to capture a
   reproducible name link process (e.g., re-use Provenance Ontology, RDA ?)
3. revisit the examples and conceive ways to establish a controlled,
   reproducible name linking process by systematically capturing the
   inputs (e.g., EOL pages ids/names + BHL texts, specimen records +
   CoL hierarchy) and outputs (e.g., a link table BHL page -> EOL page)
   as well as documenting the link process itself.
4. discuss how and where to efficiently publish / archive and distribute the
   inputs/outputs of link processes with the goal to keep track of link
   lineages
