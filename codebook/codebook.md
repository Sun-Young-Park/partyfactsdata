<style type="text/css">
h1, h2, h3 {
  color: #2c3e50;
}

body {
  text-align: justify}
</style>

**Project leaders**

-   Paul Bederke (University of Konstanz) – since 2019
-   Holger Döring (GESIS – Leibniz Institute for the Social Sciences) –
    since 2012
-   Sven Regel (WZB Berlin Social Science Center) – since 2012 </br>

**Contact**

-   Paul Bederke – <paul.bederke@uni-konstanz.de> </br>

**References**

-   Döring, Holger, and Sven Regel. 2019. “Party Facts: A Database of
    Political Parties Worldwide.” Party Politics 25(2): 97–109. doi:
    [10.1177/1354068818820671](https://doi.org/10.1177/1354068818820671)
-   Bederke, Paul, Holger Döring, and Sven Regel. 2021. “Party Facts
    Dataverse.”
    [dataverse.harvard.edu/dataverse/partyfacts](https://dataverse.harvard.edu/dataverse/partyfacts)

# Overview

**PF-Web** page
[partyfacts.herokuapp.com](https://partyfacts.herokuapp.com) //
**PF-Data** [Github
repository](https://github.com/hdigital/partyfactsdata) //
**PF-Dataverse**
[archive](https://dataverse.harvard.edu/dataverse/partyfacts)

## Credits

see full credits at [Party Facts “about
section”](https://partyfacts.herokuapp.com/documentation/about/)

Initial version of the codebook was created by Phillip Hocks and Jan
Schwalbach (University of Bremen) in 2015. This work was funded by a
small research grant of the University of Bremen ([M8
Plus](https://www.uni-bremen.de/universitaet/profil/exzellenz/)).

## Summary

The Party Facts project is a gateway to empirical data about political
parties and a modern online platform about parties and their history as
recorded in social science datasets. It makes use of social media
technologies to create a collaborative data infrastructure following an
approach to collect data successfully applied by the [Encyclopedia of
Life](https://eol.org/) (EOL).

Political scientists have accumulated a large amount of data on
political parties. This information is included in mass surveys, data
handbooks and various datasets on election results, voting records,
party characteristics and party positions. With this information we can
trace the dynamics of party competition across countries and time.
However, the many existing datasets with crucial information about
political parties are difficult to link and there is the need for a
platform that helps to combine existing sources.

With Party Facts we want to establish an infrastructure that supports
political scientists in linking parties across datasets. Our work is
based on the experience we gained in recording and linking party
information in the [Manifesto
Project](https://manifesto-project.wzb.eu/) and the
[ParlGov](http://www.parlgov.org/) project with initial data for Party
Facts derived from these two projects. In the Party Facts project we
link main datasets of political science and provide a platform for other
scientists to add party information and additional datasets.

![](codebook_files/figure-markdown_github/unnamed-chunk-2-1.png)

## Working platform

The main output and workflow of the project takes place on the [Party
Facts Website](https://partyfacts.herokuapp.com) (**PF-Web**).

Dataset imports and exports are provided in a public Party Facts Data
[Github repository](https://github.com/hdigital/partyfactsdata)
(**PF-Data**). Github is an online service for software development and
project management which allows us to coordinate, administrate and adapt
the project and datasets as a team.

Long term archiving is provided at the Party Facts Archive
[Dataverse](https://dataverse.harvard.edu/dataverse/partyfacts)
(**PF-Dataverse**).

# Parties

## Included parties

The Party Facts project aims to gather information on **all parties** in
the world which won at least **5.0%** of the votes in a national
election.

The project may add parties

-   from external datasets that won at least **1.0% of the vote**
    (preferably in two elections)
-   with a **significant leader** (prime minister, president, senior
    minister)
-   included in multiple external datasets (preferably at least three
    datasets)

The respective threshold for including and linking parties from external
datasets depends on the quality of the party level information (names,
first/last year, election results) in the external source.

We aim to avoid including small and short lived parties. If feasible, we
remove these smaller parties during the import.

Examples for additional, optional inclusion criteria of parties:

-   electoral alliances with *at least two elections* (see section
    “[Electoral alliances](#electoral-alliances)”).
-   senior minister, multiple ministers
-   below 1% vote share over a long period

## Core vs. external parties

**Core parties** are observations that have been gathered by the Party
Facts project. They can be added and edited on the Party Facts webpage.
Currently we include around **5700 core parties**.

**External parties** are observations with party information extracted
from other datasets – see [Party Facts
Data](https://github.com/hdigital/partyfactsdata). Currently we include
around **40000 external parties**.

# Countries

Party Facts covers every country in the world that is included in an
external dataset.

Currently, it includes **217 countries**. The main focus of the project
is on the national level but parties from relevant sub-national units
may be included as well, if they are covered by several datasets.

Country definitions follow **V-Dem Country Coding Units**. V-Dem does
not cover several smaller countries where we use ISO 3166-1 country code
definitions.

-   Coppedge, Michael, John Gerring, Carl Henrik Knutsen, Staffan I.
    Lindberg, Jan Teorell, and Lisa Gastaldi. 2021. ”V-Dem Country
    Coding Units v11” Varieties of Democracy (V-Dem) Project.
-   ISO 3166-1 Codes for the Representation of Names of Countries and
    their Subdivisions – Part 1: Country Codes

For some datasets we harmonize the **sub-national** or **autonomous
regions** data. This may require updating the country data in the import
script. See for example the [ParlGov
import](https://github.com/hdigital/partyfactsdata/blob/master/import/parlgov/parlgov.R)
for Greenland and Faroe Islands.

-   Northern Ireland (NIR) recoded into United Kingdom (GBR)
-   Greenland (GRL) and Faroe Islands (FRO) coded independently from
    Denmark (DNK)

# Linking

## Party links

The aim of the project is to combine and harmonize party information
from different social science datasets. Parties from external datasets
have to be linked to the corresponding core parties within the Party
Facts project. We distinguish between core parties and external parties.
**Core parties** are the party units created in Party Facts. Information
about **external parties** is extracted from the respective datasets. A
direct linking between parties of different external datasets is not
implemented and can be achieved through core party linking.

While linking a dataset to the project, please keep the following issues
in mind:

-   If possible link the party to an existing corresponding core party.
-   If the respective core party does not exist yet, please add it (see
    chapter “[Adding parties](#adding-parties)”).

## Technical links

There are other technical options for linking parties:

-   **technical** – e.g. invalid votes, blank votes, no vote, mixed vote
    etc.
-   **alliance** – electoral alliance which took part in only one
    election (see section “[Electoral alliances](#electoral-alliances)”)
-   **unknown** – parties that could not be identified (should include a
    short discussion comment)
-   **independent** – non-partisan, independent
-   **other** – category *other* in external dataset
-   **1perc** – a party winning less than 1.0% vote share in national
    elections

## Multiple links

Most external parties are linked to exactly one core party. A few
external parties may be linked to multiple core parties.

The German Greens provide an example, in Party Facts a new party is
recorded after the Greens from the West and East merged in 1993. The
ParlGov project does only record one party. Hence, this observation
(external party) needs to be linked to the two Green parties in Party
Facts (core parties).

If an external party is linked to multiple core parties we distinguish
between one **primary link** and **secondary links**. The primary link
serves as the main link whereas all other links are secondary links. It
should be linked to the core party with **the longest time overlap**.

We distinguish between the two types to make merging datasets easier and
to avoid merge ambiguities (many-to-many relationships, m:n). Initially,
the first link of an external party is set as the primary link. The
primary link for an external party with multiple links to core parties
can also be reset on the page of the respective external party. A user
comment for this party is created for any change in the primary link.

## Incomplete links

For public datasets we complete the linking of all parties that meet the
Party Facts population criteria (\>5%, see above). Public datasets are
visible on PF-Web without login and are archived regularly in the
PF-Dataverse.

For smaller parties, we may apply a staggered approach. All parties
\>5%, are linked during the initial import. Parties **\<5% and \>1%**
(or 2%) are imported but **may not be linked completely** in Party
Facts. A section “Linking status” in the “readme” of the dataset
documents the status.

**Note** – Staggered inclusion for parties \<5% introduced in March
2021. Previously, all public and archived datasets were completely
linked.

# Adding parties

If a party of an external dataset has no corresponding match among the
core parties, please add a new core party in PF-Web (login required).
This can be either achieved through the core parties list of the
respective country or through the linking section.

New core parties should include a **vote share** or seats share with its
year to identify the party. A short **description** should be included
if no share information is available (e.g. leader information: “PM Indra
Gandhi (1969-1977)” ).

## Party names

-   **Names** should be **capitalized** and cleaned with respect to
    spelling, characters etc.
-   **Alternative names** are divided by a **slash** (e.g. [All-German
    Bloc / League of Expellees and Deprived of
    Rights](https://partyfacts.herokuapp.com/data/partycodes/1010/)).
-   **Identical names** used by different parties include the **first
    year** in the English name ([Civic
    Union (1912)](https://partyfacts.herokuapp.com/data/partycodes/4507/))
-   Optional or **temporal parts** of a party name are put in
    **brackets** (e.g. [\[United\] Democratic
    Party](https://partyfacts.herokuapp.com/data/partycodes/2305/))

## Variables

-   **Name short** – Common abbreviation of the party name in the
    language of origin. If no common abbreviation is identifiable, a new
    short version is added.
-   **Name** – Name in language of origin.
    -   Different language versions in “Name” are divided by “//”.
    -   *see also* “Name other” below for non-latin and minority
        language names (e.g. [Christian Social People’s
        Party](https://partyfacts.herokuapp.com/data/partycodes/539/))
-   **Name english** – Translation of the party name into English.
-   **Name other** – Party name in languages with non-latin letters and
    for minority language names.
    -   *Required*: Indicate the name of the language followed by a
        colon
    -   Several names are divided by a semicolon.
    -   e.g. [Malayalam: ഇന്ത്യൻ യൂണിയൻ മുസ്ലിം ലീഗ്; Urdu: انڈین یونین
        مسلم
        لیگ](https://partyfacts.herokuapp.com/data/partycodes/1455/)
    -   e.g. [French: Parti populaire chrétien-social; German:
        Christlich Soziale
        Volkspartei](https://partyfacts.herokuapp.com/data/partycodes/539/)
-   **Wikipedia** – A link to the party website on the English
    Wikipedia. We use this link to download the Wikipedia data (Infobox
    and Wikidata).
-   **Year first** – Foundation of the party (usually automatically
    filled out based on source). If no information is available, the
    first election occurrence may be entered or the first year the party
    appears in an external dataset.
-   **Year last** – Dissolution of the party. If no information is
    available, the last election occurrence may be entered. Leave empty
    if the party exists as of today.
-   **Share** – Vote (or seats) share won in a national general election
    used to identify the party. Use maximum vote share if information is
    available.
-   **Share year** – Year of vote (or seats) share included in “share”.
-   **New** – Genuinely new party, not formed through party change.
-   **Description** – Further information about the party
    (e.g. evolution, name changes etc.).
-   **Comment** – Comments about the coding to the party. May also
    include party relations such as predecessor, successor, name
    changes, mergers and alliances.
-   **Data** – Additional data in
    [JSON](https://en.wikipedia.org/wiki/JSON) as a collection
    name–value pairs in an object. (e.g. ‘{“inclusion”: “leader”}’)

## Deleting parties

Observations (parties, links, etc.) may be removed by any user due to
coding mistakes or duplicates. It is important to **give a short reason
for deleting** an observation in the comment to document the coding
decision.

# Alliances and changes

## Electoral alliances

We record only electoral alliances that take part in **at least two
elections**. All other (one term) electoral alliances are linked to the
“alliance” category – see section “[Technical links](#technical-links)”.

An electoral alliance included in at least **three other datasets** may
be added as well.

Core parties that form an electoral alliance included in Party Facts can
be recorded in the following format

-   Electoral alliances may include a comment:
    -   consists of `<PartyFactsID1>` `<PartyFactsID2>`
    -   e.g. [Front of National
        Unity](http://partyfacts.herokuapp.com/data/partycodes/4473/)
-   Alliance members (core parties) may include a comment:
    -   member of `<PartyFactsID>`
    -   e.g. [Polish United Workers’
        Party](http://partyfacts.herokuapp.com/data/partycodes/1286/)

## Party changes

*Note — Coding of party changes and party names incomplete.*

Relations between parties are shown on the core party’s page, containing
**successor and predecessor** parties.

Renamings of parties are recorded in the description:

-   `<year>` `<name_english>` (`<name [optional]>`, `<name_short>`)
-   e.g. [Left Party / Communist
    Party](http://partyfacts.herokuapp.com/data/partycodes/830/) ·
    Sweden

Additionally the new (or respective old) name of the party may be added
to the party name by using a slash to divide the names. Please see
chapter “[Adding parties](#adding-parties)” for further instructions.

# Validation

As a measure to review existing party links, users are able and
encouraged to validate links of other users. An active validation of
information is an important part of the project. Based on the party
names and (roughly) matching dates, a quick validation is often
possible. Otherwise the information given about election results may
provide additional help.

While reviewing established party linkings there are several options
applicable:

-   **positive link** – I validate the already made link.
-   **negative link** – I doubt link is valid but am not sure and others
    shall make the verdict.
-   **comment (+ negative link)** – here are my reasons – not daring to
    remove it right away.
-   **remove link** – I know what I am doing

You can remove your validation by clicking the highlighted
validate-button again. Negative validations are summarized and reviewed
on the [recent
linking](https://partyfacts.herokuapp.com/activity/linking/) page.

# Datasets

In Party Facts we collect party level information from external
datasets. We do not include these external datasets but **extract party
information only**. Therefore different datasets from the social
sciences are linked but are not combined. Currently around **60 external
datasets** are imported and around **40000 external parties** are
linked.

## Categories

Datasets are grouped into different categories depending on their
connection to the Party Facts project, the number of parties they cover
and their relevance for social science research.

*Core members* are datasets, which formed the foundation of the project.
*Partner projects* include those datasets with whom the project has
cooperated. *Main datasets* contain datasets with a wide scientific
reach. Datasets which were recently included or with remaining technical
problems are grouped under *experimental*. Any user can import a
(scientific) dataset as a *user dataset*.

Currently we include the following categories for
[datasets](https://partyfacts.herokuapp.com/documentation/datasets/):

-   **Core member:** ParlGov, MARPOR
-   **Partner project:** CLEA, CHES, EJPR-PDY, V-Party
-   **Main dataset**
-   **All dataset**
-   **Article dataset**
-   **Experimental dataset:** initial import of datasets (login required
    in PF-Web, not archived in PF-Dataverse)
-   **User dataset** (login required in PF-Web, not archived in
    PF-Dataverse)
-   **Test mapping:** explore interface

## Included datasets

Please note that party information from the respective datasets are only
included into Party Facts and may not yet be completely linked to core
parties.

For each dataset in Party Facts we document the following information
and variable names.

-   **key** – A unique key (letters and numbers only) identifying the
    dataset. This key is the same as the folder name of the dataset in
    the PF-Data Github repository.
-   **type** – The type of the dataset and its connection to the Party
    Facts project – **see above**.
-   **name** – Name of the dataset as it appears on the website.
-   **reference** – A reference for the dataset to be used for citing
    the source ([APSA style
    guide](https://connect.apsanet.org/stylemanual/references/)).
-   **url** – Dataset webpage (if available).
-   **description** – A short summary of the party level information
    included in the dataset.
-   **comment** – Additional information about the dataset (not
    required).
-   **Year first** – First observation year of the dataset.
-   **Year last** – Last observation year of the dataset.

Variable names used to import party information from dataset into Party
Facts.

-   **Var country** – Country ISO-code.
-   **Var code** – Unique identifier of party in the dataset.
-   **Var name short** – Abbreviation of the party name.
-   **Var name** – Name of the party in language of origin.
-   **Var name english** – Name of the party in English.
-   **Var year first** – Year of first observation of a party.
-   **Var year last** – Year of last observation of a party.
-   **Var share** – Share of a party in an election.
-   **Var share year** – Year of the respective share in “Var share”.
-   **Var description** – Further remarks.
-   **Var comment** – Further comments.

## Information on datasets

For further information about the content of different datasets
(e.g. number of parties, countries, time span etc.) and the respective
projects, see [datasets
overview](https://partyfacts.herokuapp.com/documentation/datasets/).

## Available downloads

Party Facts offers two different datasets, which are directly available
in the PF-Web [download
section](https://partyfacts.herokuapp.com/download/) and in the
PF-Dataverse.

The dataset **Datasets parties** contains all external parties currently
included and linked in Party Facts. The information covers:

-   **country** – ISO-code of the country.
-   **dataset_key** – Abbreviation of the dataset name.
-   **dataset_party_id** – unique key of party in external dataset. //
    **used for merging**
-   **name_short** – Common abbreviation of party.
-   **name** – Name of party in language of origin.
-   **name_english** – Name of party in English.
-   **year_first** – First observation of the party.
-   **year_last** – Last observation of the party.
-   **share** – Result in a parliamentary election.
-   **share_year** – Year of the election result.
-   **description** – For further description.
-   **comment** – Section for comments.
-   **created** – Date of creation in Party Facts.
-   **modified** – Date of last modification.
-   **external_id** – Unique numeric id of external party in Party Facts
    database.
-   **partyfacts_id** – Party Facts identification number. // **used for
    merging**

The dataset **Core Parties** contains all Party Facts’ core parties with
the following information:

-   **country** – ISO-code of the country.
-   **partyfacts_id** – Party Facts identification number.
-   **technical** – Technical identification number the party has been
    linked to.
-   **name_short** – Common abbreviation of party.
-   **name** – Name of party in language of origin.
-   **name_english** – Name of party in English.
-   **name_other** – Party name in languages with non-latin letters.
-   **year_first** – Foundation of the party.
-   **year_last** – Dissolvement of the party (blank if still existing).
-   **share** – Result in a parliamentary election.
-   **share_year** – Year of the election result.
-   **new** – Genuinely new party.
-   **wikipedia** – Link to the respective Wikipedia homepage.
-   **description** – For further description.
-   **comment** – Section for comments.
-   **created** – Date of creation in Party Facts.
-   **modified** – Date of last modification.

The download section provides merge examples in R and Stata.

# Importing data

In general everyone can add a dataset to the project. But please make
sure that the dataset fits the following criteria:

-   Only datasets with a scientific background are added to Party Facts
-   The dataset should contain the following information as variables.
    (For detailed information see chapters “[Adding
    parties](#adding-parties)” and “[Datasets](#datasets)”)
    -   English name
    -   Name short
    -   Original name
    -   First year
    -   Last year
    -   Max share
    -   Share year
    -   Country name short
-   We import the dataset in csv format **(utf-8)**. If your dataset has
    a different format, you may convert it into csv **(utf-8)**. Hence
    the import is done via an R scripts and the final data must be in
    csv format.

Ideally, a dataset is prepared by a user for an import into Party Facts.
A step-by-step guide on how to import a dataset into the Party Facts
project can be found in the PF-Data [Github
repository](https://github.com/hdigital/partyfactsdata) of Party Facts.
It allows you to prepare your dataset for an import into the Party Facts
project and to link your dataset to other well-known scientific
datasets.

An import of a prepared dataset into the database at partyfacts.org is
done by the project maintainers.

External parties with a **unique match** of a party name (name short,
original name or English name) or a **“partyfacts_id”** are
**automatically linked** during the import into the database.

If you have further questions, please contact the project coordinator.

# Comments and user interaction

We use [comments](https://partyfacts.herokuapp.com/activity/comment/)
for party specific coding information, user interaction, issue tracking,
to highlight potential mistakes and to discuss coding issues (PF-Web
login required).

To address open issues and questions with respect to the linking of
parties or information about parties, please use the discussion section
below each party (core and external). To address single users
(e.g. concerns regarding a particular linking), @<Partyfactsusername>
can be used.

In the *activity section* an overview of the
[comments](https://partyfacts.herokuapp.com/activity/comment/) is
displayed. Please mark a comment as solved if it does not need a review
by another user.

Use comments if you can’t solve an issue yourself or are not sure about
the application of the coding rules (e.g. re-linking a party, updating
core parties information).

We review all comments and mark them as solved once the issue has been
addressed.

# Changes

### Codebook

2021-12-07

-   update contact information
-   update references
-   minor revision

2021-07-29

-   include logo

2021-03-09

-   add/revise inclusion criteria for electoral alliances
-   revise format of naming history in description field
-   add region information and examples (NIR, GRL, FRO)
-   round number of core parties
-   APSA style guide reference
-   add example for *name other*
-   minor revisions

2020-07-17

-   change codebook into RMarkdown file
-   add minor general information
-   add worldmap.png
-   remove some broken links

2020-07-12

-   add inclusion criteria for parties with significant leaders

2020-06-08

-   update reference Party Politics article

2019-11-28

-   add Paul Bederke as project member

2019-06-07

-   specify delimiter for different languages in party “Name” (“//”)
-   replace “eg.” with “e.g.”

2019-06-07

-   add Dataverse reference
-   add Paul Bederke contribution

2019-01-11

-   add Party Politics project reference

2018-10-09

-   highlight key concepts in bold
-   revision dataset categories section

2018-09-24

-   minor revisions and specifications for Comments/Interaction section

2018-08-22

-   add definition core/external parties
-   update information about Wikipedia link
-   update Github url to repo name “partyfactsdata”
-   minor revisions

2018-06-18

-   inclusion of electoral alliance members optional

2017-04-04

-   more specific information about inclusion threshold external parties

2017-06-18

-   added information on linking of unique names during import

2017-03-16

-   added documentation of country definition

2016-09-19

-   more specific and unified information about party naming

2016-05-01

-   updated country list: added countries from V-Dem, some name clean-up

2016-02-02

-   added dataset type “article”

2016-01-04

-   documentation of party change implementation
-   update order of columns in data to download

2015-11-18

-   initial version by Phillip Hocks and Jan Schwalbach

### Data (revisions)

2021-07-15

-   completed removal of about 100 duplicates

2021-03-08

-   recoded NIR parties into GBR
-   harmonized dataset descriptions with categories
-   converted data fields (PartyAll, Trash) into PostgresSQL jsonb
-   added data field (JSON format) to core party model

### Data (robot)

Documentation of automatic data changes since November 2018 (user
robot).

2021-03-08 — 2021-03-13

-   updated core parties share information using linked external parties
    share (esp. V-Party)
-   removed “ParIS” entry from *description* and *comment* field in core
    parties (around 1000)
-   renamed “Prime Minister” into PM in core party *description* field
-   replaced “–” with “—” in *name* and *name_english* field in core
    parties (around 50)
-   updated “year_last” with “dissolved” from Wikipedia element

2018-11-17

-   removed (some) redundant share information in description or comment

2018-11-11

-   removed parties not meeting inclusion criteria (around 170)

2018-11-03

-   update PPLA default dates to 2006 / 2007
