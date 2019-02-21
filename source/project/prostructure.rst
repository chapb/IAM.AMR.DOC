

Project Structure
=================

Goals
-----
The overall goal of the IAM.AMR project is to elucidate and quantify the relative contributions of specific agri-food commodities and related environmental exposure pathways to Canadians’ overall exposure to antimicrobial resistant bacteria arising from the agri-food production system. To meet this goal, we endeavor to:

* create a conceptual model describing the agri-food production system, the drivers of AMR within this system, and the effects of AMR within this system (and beyond) on human, animal, and environmental health.
* collect data from national AMR and AMU surveillance programmes, associated research projects, and the scientific literature to describe the ecology and epidemiology of AMR in this system historically, and at present.
* quantify the individual effect of each driver of resistance -- and identify omitted drivers -- through a comprehensive literature search.
* integrate the conceptual model, epidemiological data, and the effect of each driver within a standardized modelling framework.
* use the developed mathematical model(s) to understand how drivers, such as AMU and Canadian production practices affect human exposure to antimicrobial resistant bacteria arising from the agri-food production system.
* engage industry stakeholders to inform identified knowledge gaps, communicate high-risk practices, and provide recommendations considering each human, animal, and environmental health.
* use these findings to inform broader AMR human risk-reduction initiatives.

Overview
--------
An overview of the entire project can be accessed via Kumu via the `AMR Org Chart <https://kumu.io/chapmanb/amr-org-chart>`_, embedded below.

.. raw:: html

  <iframe src="https://embed.kumu.io/e315cfc80b9406550b1aab93f436440b" width="705" height="450" frameborder="0"></iframe>

To edit or contribute, please contact Brennan Chapman.

Scope
~~~~~
To reduce the scope of the project to a manageable size, the three most common food-animal species and the three most commonly isolated enteric bacteria from those species were selected as the core areas of focus. These include chicken, cattle, and swine, and E. coli, Salmonella Spp. and Campylobacter Spp. for host species and bacterial species respectively. While the primary human exposure route is assumed to be consumption of the corresponding agri-food products (chicken, beef, and pork), additional focus has been placed on environmental exposure routes (e.g. through the consumption of leafy greens or root vegetables, grown in manure-amended soils).

Additional food-animal and bacterial species of interest include turkeys and Enterococcus Spp., which may be explored later as the project progresses. 

Organization via stories
++++++++++++++++++++++++
The models are organized primarily by ‘stories’, or bug-drug-host combinations of particular interest. Existing stories and their corresponding models are available in the IAM.AMR GitHub repository. 


Literature Search
~~~~~~~~~~~~~~~~~
The IAM.AMR models are informed by a single, all-encompassing literature search. A description of the literature search and associated products is provided on the :ref:`literature search main page <project/search:Literature Search>`.

The CEDAR database
~~~~~~~~~~~~~~~~~~
CEDAR, the Collection of Epidemiologically Derived Associations with Resistance, is a Microsoft Access database, designed to house data extracted in support of the IAM.AMR project and associated activities.

The studies identified through the literature search are reviewed, and data extracted as per a number of criteria outlined on the :ref:`CEDAR main page <project/cedardb:The CEDAR Database>`.

The cedarr package
~~~~~~~~~~~~~~~~~~
The cedarr package is an R package which processes queries extracted from the CEDAR database. The package is fully documented in-line using Roxygen2, and is outlined on the :ref:`cedarr main page <project/cedarr:The cedarr Package>`.

Model Building
~~~~~~~~~~~~~~
Once the data are extracted from the literature, collated in -- and queried from -- the database, and processed by the R package, they are included in a model built around a robust model framework.

The IAM.AMR models are designed to predict the frequency of exposure of Canadians (and specifically, Ontarians) to antimicrobial-resistant bacteria from agri-food products. To do so, the models follow agri-food production along the farm-to-fork continuum – where possible, from birth (or hatch), through rearing, slaughter, processing, retail, and finally human consumption.

The models start with a baseline prevalence of resistance, derived from the earliest sampling point we have available – ideally as close to birth (or hatch) as possible. This prevalence of resistance is affected by practices at each stage of production; we term these practices ‘factors’ which affect resistance. These factors are grouped by stage of production: on-farm, at abattoir, and at retail. 

.. note:: The models only include binary factors (i.e. those described by yes or no). This means that a factor may be considered in one of two ways: as a risk (i.e. it increases the prevalence of resistance) or as being protective (i.e. it decreases the prevalence of resistance). It is important to note that this perspective (risk vs. protective) depends on the scenario. For example, changing the litter material of broiler chickens from straw to wood curls may increase the prevalence of resistance (a risk) – but if we have a scenario in which all litter material is already wood curls, this factor is only informative when we flip it, and consider the protective effect of changing the material to straw.

At each stage of production, we take the prevalence of resistance from the previous stage (e.g. baseline for on-farm, on-farm for abattoir, etc.) and update it, considering the effect of each factor (in combination with all others), and how often that factor is implemented in Canadian industry. We then pass this updated prevalence of resistance to the next stage. The calculations used to update the prevalence at each stage are identical, though as you will likely notice, we have more factors at the on-farm stage than any other.

After calculating the final prevalence of resistance at retail, we use the prevalence of bacterial contamination at retail (i.e. the recovery rate of the bacteria, derived from national surveillance programmes), estimates of population size, and consumer consumption behaviours, to derive the final output of the model -  the number of servings of the agri-food product that are contaminated with antimicrobial-resistant bacteria in a one week period


Funding and History
-------------------
Stakeholders from each human, animal, and environmental health disciplines are often engaged in addressing the risk posed by AMR in the agri-food production system. A project [#Majowicz]_ by an associated team aimed to identify non-traditional stakeholders, who are often overlooked for engagement, but are nonetheless affected by AMR. As part of this project, the team created a large diagram of drivers, included below.

.. figure:: /images/majfig2.png
   :align: center

   Figure 2 from Majowicz et al. (2018) demonstrating the complexity of the drivers of AMR.

The IAM.AMR project was born out of the concept of enumerating these identified pathways. Beginning in 2014, the IAM.AMR project was supported by the Ontario Ministry of Agriculture, Food and Rural Affairs (OMAFRA) New Directions Funding Program (Project ND2013‐1967), with a focus on the applicability of the models specifically to Ontario (a focus that remains today). Subsequently, the project has been continued as a sub-project of GRDI-AMR.

.. [#Majowicz] Majowicz, S.E., Parmley, E.J., Carson, C. et al. BMC Res Notes (2018) 11: 170. https://doi.org/10.1186/s13104-018-3279-8

GRDI
~~~~
The Genomics Research and Development Initiative (`GRDI <http://grdi-irdg.collaboration.gc.ca/eng/index.html>`_) funds genomic research across the federal science portfolio. A specific focus of GRDI is the development of shared priority projects (i.e. projects involving multiple federal departments). The GRDI-AMR project (2016 – 2021) is a nine million dollar shared priority project lead by Ed Topp at AAFC, which aims to use genomics to understand how the development of AMR in the agri-food production system impacts human health. 

The project is broadly divided into five working groups; the IAM.AMR project is a significant, evergreen deliverable from work package five.

