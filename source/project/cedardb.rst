

The CEDAR Database
==================

Introduction
------------
CEDAR, or the Collection of Epidemiologically Derived Associations with Resistance, is a Microsoft Access database designed to facilitate the extraction and retrieval of data relevant to the IAM.AMR project. 

What is a database?
~~~~~~~~~~~~~~~~~~~
A database is simply a collection of data, organized a way that makes it easy to search for, select, and retrieve specific subsets of information. CEDAR is a relational database, which means our data are split logically across different tables, linked together by relationships between common fields. By taking the time to separate our data into individual tables and define these relationships, we can ask complicated questions of our data, while reducing the amount of redundant or duplicate information that we must extract and store.

.. note:: Technically, a "database" is simply a collection of data, and the "database management system" is the software we use to create, manage, and access that data. However, the term "database" is used colloquially to refer to both the data itself, the software, and the forms and reports we use to enter and extract the data respectively.

How does a database differ from a spreadsheet?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Take a look at the table below that includes demographic and political information for some of Canada’s largest cities. This represents a traditional *flat-file* or spreadsheet approach.

==========  ==========  ==========  ==========  ==========
Province    Premier     Party       City        Population
==========  ==========  ==========  ==========  ==========
Ontario     Ford        CPC         Toronto     2,700,000
Quebec      Legault     CAQ         Montreal    1,700,000
Alberta     Notley      NDP         Calgary     1,200,000
Ontario     Ford        CPC         Ottawa      934,000
Alberta     Notley      NDP         Edmonton    932,000
Ontario     Ford        CPC         Mississ...  721,000
==========  ==========  ==========  ==========  ==========

What you may notice is that there are two drawbacks to this approach. The first is that there are many duplicate values -- some poor research assistant had to input “Ontario”, “Ford”, and “CPC” three times. This increases the size of our database, increases the amount of time required for data entry, and is prone to errors.

The second drawback is that out table does not serve a single logical purpose -- if you had to title it, what would that title be? The table includes a mix of provincial-level and municipal-level data that are not directly related, so why should they be in the same table?

A relational database approach would involve splitting these two tables into unique entities, and linking them via a common field:

==========  ==========  ==========  ==========  
ID          Province    Premier     Party     
==========  ==========  ==========  ==========
01          Ontario     Ford        CPC       
02          Quebec      Legault     CAQ       
03          Alberta     Notley      NDP          
==========  ==========  ==========  ==========

==========  ==========  ==========
Prov. ID    City        Population
==========  ==========  ==========
01          Toronto     2,700,000
02          Montreal    1,700,000
03          Calgary     1,200,000
01          Ottawa      934,000
03          Edmonton    932,000
01          Mississ...  721,000
==========  ==========  ==========

Now, each table represents a single theme or purpose, and we’ve dramatically reduced the number of times we’ve had to enter error-prone data by replacing multiple fields with a single ID number. CEDAR takes this type of approach, but with a more complex data structure.

What is some basic database terminology?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
A **database** is a collection of **tables**, linked together by defined **relationships**.

Tables, like those in a spreadsheet, consist of rows and columns. Each row also known as a **tuple** or **record**, is a set of data which represents a single item. This set of data consists of multiple named pieces of data, known as **attributes** or **fields**, which are organized into columns. In our examples above, each row is a set of data corresponding to a major city. Each set of data has individual data points, corresponding to the headings (or fields) of our table.

A **form** is how we enter data into the database. It is a graphical, easy-to-use way of entering data across many tables at once. In the example above, we might have a simple form to allow users to enter the population size, with a pre-filled dropdown menu of provinces to make data entry faster. A **query** is a request we pass to the database to retrieve a specific subset of records and fields, constrained by criteria we specify. In the example above, we might query the database, asking the question “which premiers preside over regions with cities exceeding one million people”. 

What is not covered in this documentation?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
There are a number of advanced concepts and workflows that this documentation simply cannot reasonably describe, including designing forms, designing queries, directly accessing and modifying tables, adding non-relevant references, adding meta-analysis meta-data, making edits where data were improperly entered, adding items to dropdowns, etc.

When in doubt, or if an advanced change would make your life easier, contact the database administrator.


Opening the Database
--------------------

Understanding the database files
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The CEDAR database consists of two separate and distinct files. The first (and most important) is the *back-end* file. This is the central repository where data is actually stored -- it remains in the same location, on PHAC's network, at all times. The second is the *front-end* file, through which we input, retrieve, and manipulate data. You can think of these front-end and back-end files like a web browser and a website respectively -- the website contains the data, and you access it through the browser. And, just like we can access a website through many browsers, at many locations, we can access the back-end through many versions of the front-end, and on our individual computers. So when we refer to “opening the database”, what we actually mean is opening the front-end file, to interact with the data in the back-end file.

.. note:: If the database is distributed outside of PHAC, the back may be combined into a . There is little to no difference in the appearance 

Opening the front-end file
~~~~~~~~~~~~~~~~~~~~~~~~~~
Upon opening CEDAR, you’ll be presented with a mostly blank screen:

.. figure:: /images/cedar_overview.PNG

On the left hand side, all of the database objects are grouped by type in the Navigation Bar. As previously described, these objects include tables (raw data), queries (specific subsets of data), and forms (interfaces to view and add data).

Re-linking the database files
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
To continue our website analogy, while the front-end file is entirely portable (like a web browser on a laptop), the back-end file must never move (like Google, or Facebook). However, just like the path to Google is slightly different based on the country you’re in (e.g. https://google.com in the USA, https://google.ca in Canada), the path to the database is slightly different based on your roll at PHAC. Therefore, when you receive a front-end file, we may have to *re-link* this file with the back-end.

How will you know you need to re-link the database? You’ll see an error like this when opening on a table, query, or form:

.. figure:: /images/cedar_unlink.PNG

To re-link the files:

* In the ribbon at the top of the screen, select the *External Data* tab, and then select *Linked Table Manager*. Accept the security notice (if prompted).
* On the right-hand side of the *Linked Table Manager*, select *Select All*, and then *OK*.
* An explorer window will open. Navigate to, and select the back-end file.

When complete, save the file (using CTRL-S, or the save icon in the upper left corner) to skip the re-linking process in the future.

.. tip:: You will have to complete the re-linking each time a new version of the front-end file is distributed.


Accessing the Main Form to View and Enter Data
----------------------------------------------

The Main Form [Data Entry (Main)] is a combination of two individual forms, highlighted below. The left panel of the form is related to study-level information, and is further broken down into several tabs. The right-panel of the form is related to factor-level information, and is formatted as a continuously scrolling list.

.. figure:: /images/cedar_form.PNG
   
   1: The left panel relates to study-level information. 2: The right panel is a continuously scrolling list of factor-level information.

The form is designed to be as straightforward as possible. The contents of each field are described in the data dictionary, along with specific formatting preferences and requirements. However, the easiest way to understand the purpose of a given field is to look at one of the existing examples.

INSERT DATA DICTIONARY

A brief description is also available in the Status Bar (in the lower left corner), when the cursor is placed in the field, and as a control tip when the field is hovered-over.




Roles Covered
--------------

Data extraction




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

Including comparisons between sampling period where nothing has changed other than time. Location.

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
