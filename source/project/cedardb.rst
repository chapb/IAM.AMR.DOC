

The CEDAR Database
==================

Introduction
------------
The Collection of Epidemiologically Derived Associations with Resistance (CEDAR) database is a Microsoft Access database designed to facilitate the extraction and organization of data relevant to the IAM.AMR project.

Previous Approach
~~~~~~~~~~~~~~~~~

Why a Database?



Opening the Database
--------------------
The CEDAR database consists of two separate and distinct files. The first (and most important) is the *back-end* file. This is the central repository where data is actually stored -- it remains in the same location, on the network, at all times. The second is the *front-end* file, through which we input, retrieve, and manipulate data. You can think of these front-end and back-end files like a web browser and a website respectively -- the website contains the data, and you access it through the browser. And, just like we can access a website through many browsers, at many locations, we can access the back-end through many versions of the front-end, and on our individual computers. So when we refer to “Opening the Database”, what we actually mean is opening the front-end file.

.. note:: When the database is distributed outside the organization, these files may be combined for ease-of-use.

To continue our website analogy, while the front-end file is entirely portable (like a web browser on a laptop), the back-end file must never move (like Google, or Facebook). However, just like the path to Google is slightly different based on the country you’re in (e.g. https://google.com in the USA, https://google.ca in Canada), the path to the database is slightly different based on your roll at PHAC. Therefore, when you receive a front-end file, we may have to *re-link* this file with our back-end.

How will you know you need to re-link the database? You’ll see an error like this:

INSERT PICTURE

Re-linking the Database
~~~~~~~~~~~~~~~~~~~~~~~
* In the ribbon at the top of the screen, select the *External Data* tab, and then select *Linked Table Manager*. Accept the security notice (if prompted).
* On the right-hand side of the *Linked Table Manager*, select *Select All*, and then *OK*.
* An explorer window will open. Navigate to, and select the back-end file.

When complete, save the file (using CTRL-S, or the save icon in the upper left corner) to skip the re-linking process in the future.

.. tip:: You will have to complete the re-linking each time a new version of the front-end file is distributed.

A note about data
-----------------
BE AWARE that you are accessing live data! Any changes you make are instantly reflected in the database (there is no save required to confirm changes), and modified data can not be readily recovered. Please take care not to erroneously modify or delete data.


Navigating the Database
-----------------------

Opening the Form
~~~~~~~~~~~~~~~~

differentiate the record from each in the sub table.

Elements of the Record
~~~~~~~~~~~~~~~~~~~~~~

Moving through records
~~~~~~~~~~~~~~~~~~~~~~
To view the entered data, use the arrows at the bottom of the screen to change between records – the official term for entries in a database. 

Search
~~~~~~

To skip to a particular record (reference), first place the cursor in the Short Name field, and then use the search bar at the bottom of the screen. Note that this search is somewhat finicky -- it will look for occurrences of your search term in the current record first, then jump to other records. Therefore, after entering your term, you may have to use the Enter Key to continue through these matches until you find the correct record.


Adding New Records
------------------
A new reference can be added to the database, either by scrolling past the last record (reference) or by using the *New Record Button* (right arrow over yellow asterisk) at the bottom of the screen.

Add a Short Name
~~~~~~~~~~~~~~~~
The only absolutely required piece of information (that Access will loudly complain if you forget) is the Short Name -- it's the identifier that links all tables in the database.

The Short Name should be defined as follows:

FirstAuthor et al. (year)

If there is more than one publication for the same author, append a letter as follows:

- FirstAuthor et al. (Year)a
- FirstAuthor et al. (Year)b

.. tip:: If you  

Fill in the Remainder of the Bibliographic information
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Assumptions
* Do not worry about listing assumptions such as those listed below, as they to be made at the project level:

  * Assumed to reflect the Canadian context
  * E. coli is assumed to behave like Salmonella




Fill in the Factor information
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
-	Extract count data with no decimal places, and extract percentages to one decimal place
-	If no measure of statistical significance (e.g. P-Value) is reported, put “NR” to indicate that in the significance field

Priority
++++++++
We prefer count data (2-by-2, or contengency table) information over percentages if both are available. However, do not convert one to the other.


Roles Not Covered
-----------------

Designing Queries, Adding Meta-analyses, Directly addeing tables/records, changes lik ethat.


Roles Covered
--------------

Data extraction

note that they can see the field descriptors in the menu bar!



Data extraction rules
---------------------
This section describes the data extraction rules the guide the inclusion or exclusion of factors in/from the CEDAR database. The process of data extraction is always a balance between comprehensiveness and feasibility -- it is simply impossible to extract every piece of data from each study.

It should be noted that these rules were not created *a priori* -- they were a result of decisions arising from challenges as data extractors progressed through the collected body of literature. As a result, new rules were established at different stages of the literature review and data extraction process. Where possible, we have reviewed previously examined studies to re-apply these rules, and ensure all qualifying factors were extracted. However, we have been less stringent on eliminating information from the database for factors which may no longer qualify for extraction.

Only binary factors are extracted
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Where a factor is continuous, it must not be extracted. Where a factor has multiple levels, multiple factors should be extracted comparing the referent and defined levels, except ...

... where a level is not informative.

   For example, where the levels are 'A (referent)', 'B', 'C' and 'Other', and 'Other' is undefined. The factors A-B, A-C should be extracted. The factors B-C and A-Other should not be extracted.

However, where an otherwise uninformative level makes it binary (yes, no or other), it shall be extracted. e.g. ceftiofur vs none or other.



All antimicrobial resistances are extracted
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Factors related to any antimicrobial resistance should be extracted (including ionophores, coccidiostats, and metals), except ...

... where the use is specified only as MDR.

In cases where multiple AMs were used in the past, or as part of generic practices, not captured as an experimental element (e.g. no regression, comparison of multiple control groups), those factors will noit be extracted.

Multiple measurements at single stage
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Where multiple measurements are available within a single stage, the measurement closest to human exposure should be extracted, except ...

... where there are missing or unavailable data at the measurement closest to human exposure.
   
   For example, where an observation is missing from one treatment group, or where multiple experiments end at different time points. The measurement that is closest to human exposure that is comparable across experiments or within an experiment should be extracted.

... where the data is inapplicable in the Canadian context.

   For example, where an observation is recorded after production would have ended in Canada. The measurement that is closest to human exposure that is within production timelines should be extracted.

... where a cross-over or other study design feature results in different exposures.

   For example, where an observation is recorded after the cross-over. The measurement that is closest to human exposure, whose effect is attributable only to the treatment should be extracted. A seperate factor may be extracted for the treatment after cross-over.

.. tip::   
   Resistance was assayed at days 10, 20, and 30 of production. Measurement from day 30 is extracted.

   Resistance was assayed at days 10, 20, and 30 of production for the treatment group, and at days 10, and 20 for the referent group. Measurement from day 20 is extracted.

   Resistance was assayed at days 7, 14, 21, 28, 35, 42, and 49 of broiler production. Measurement from day 35 is extracted, as it is the latest within the Canadian production timeline of 36 days.

   Resistance was assayed at days 7, 14, 21, 28, 35, 42. A cross-over occured after measurement on day 28. Measurement from day 28 is extracted. Measurement from day 42 may be extracted, where referent is day 28.

Measurements at Mul;tiple stages
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In the event that measurements are taken across stages, the measurement closest to human exposure shall be extracted, within the effective stage.


Selective Media
~~~~~~~~~~~~~~~
Where measurements are available for both selective and non-selective media, the measurement on non-selective media should be extracted. Where results are not presented for non-selective media, the selective media shall be extracted.

Genotype
~~~~~~~~
Where measurements of resistance are based on genotype and phenoytpe, both measurements must be extracted, to enable genotypic phenotypic models to be created in future.



Poor effect time
~~~~~~~~~~~~~~~~
Where a measurement occurs too soon or too long after an exposure, such that the measurement is unlikely to reflect the exposure, the measurement should not be extracted.


Immutable Factors
~~~~~~~~~~~~~~~~~

Including comparisons between sampling period where nothing has changed other than time. Location (outside canada).

Levels of Abnalysis
~~~~~~~~~~~~~~~~~~~
If two levels of analysus are available (e.g. flock vs animal), the finer shall be recorded.

Campylobacter
~~~~~~~~~~~~~
Where a study breaks down Campylobacter by type, all data should be collected. However, do not collect the combined information.







Generating queries
------------------



Required Fields
~~~~~~~~~~~~~~~
-	[Reference Name]
-	[DOI]
-	[Population]
-	[Sub-population]
-	[Genus]
-	[Species]
-	[Stage]
-	[Resistance]
-	[Title]
-	[Definition]
-	[Exposed Group]
-	[Referent Group]

- Core Table
   
   - [A], [B], [C], [D]

- Marginal Table
   
   - [P], [Q], [M1], [M2]

- [Odds Ratio]
- [Odds Ratio – Lower Confidence Interval]
- [Odds Ratio – Upper Confidence Interval]
- [Odds Ratio – Significance]
- [Outcome Format]
- [Meta-analysis ID]
- [Meta-analysis Resistance]
- [Exclude IAM?]

Meta-analyses in CEDAR
----------------------
Meta-analysis is a statistical approach for combining data from multiple studies, often used to increase statistical power, or resolve uncertainty in effect size or direction. The simplest way to think of a meta-analysis is as a weighted average of the included observations, where the weighting accounts for the statistical properties of the studies. 

Meta-analysis is used in the IAM.AMR project to derive a single effect estimator where multiple studies, or multiple observations within a study, are available to describe a given factor.

When should meta-analysis be performed?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Meta-analysis must only be performed where the effect measure, and the study populations, are identical or highly similar. Therefore, meta-analysis should **never** be performed:

* across food-animal species (species)
* across bacterial species (pathogens)

   * including between Campylobacter jejuni and conventional

* across classes of antimicrobials
* across classes or sub-classes of antimicrobials

  * excluding NAL and FQs?

* across production stages
  
  * this includes where the effective stage is the same, but the measurement is taken at a different stage.
  

When a measurement is available for the same stage of production, the same food-animal, pathogen, and antimicrobial (or sub-class of antimicrobial), as one or more others, they may be included in one of four types of meta-analysis: 

Within Study, Same Antimicrobial
++++++++++++++++++++++++++++++++
Where multiple measurements are available describing the same factor, for the same resistance, the measurements should be combined using meta-analysis.
   
.. tip:: 
   Two comparable sub-populations comprise the study population (e.g. barn A and barn B), and ceftiofur resistance is assayed for each. Meta-analysis is conducted for these observations.

Within Study, Same Antimicrobial Class (or Sub-Class)
+++++++++++++++++++++++++++++++++++++++++++++++++++++
Where multiple measurements are available describing the same factor, for the same class or sub-class of resistance, the measurements should be combined using meta-analysis. 

.. tip::
   Resistance to ceftiofur and ceftriaxone are both included in the assay. Meta-analysis is conducted for these observations, and the resistance is reported at the sub-class level (third-generation cephalosporin resistance).

   Resistance to ceftiofur and ceftriaxone are both included in the assay, and there are two comparable sub-populations which comprise the study population. Meta-analysis is conducted for all of these observations, and the resistance is reported at the sub-class level (third-generation cephalosporin resistance).

Across Studies, Same Antimicrobial
++++++++++++++++++++++++++++++++++
Where multiple measurements are available describing the same factor, for the same resistance, and the experimental conditions are comparable, the measurements should be combined using meta-analysis.

.. tip::
   Two studies measure the effect of production type (e.g. organic vs. conventional) on ceftiofur resistance. Meta-analysis is conducted for these observations.

Across Studies, Same Antimicrobial Class (or Sub-Class)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
Where multiple measurements are available describing the same factor, for the same class or sub-class of resistance, and the experimental conditions are comparable, the measurements should be combined using meta-analysis.

.. tip::
   Two studies measure the effect of production type (e.g. organic vs. conventional), one on ceftiofur resistance, and the other on ceftriaxone resistance. Meta-analysis is conducted for these observations.


How is the meta-analysis performed?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Where multiple measurements are identified as qualifying for inclusion in a meta-analysis, the records are tagged within the CEDAR database by an administrator. When these records are retrieved by a query, and submitted for processing using the cedarr package, a random-effect meta-analysis is automatically performed, and the original records are optionally dropped from the output.

If you identify a record which should be included in a meta-analysis, please notify a CEDAR administrator. 
