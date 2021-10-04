# README #

Copyright © 2021 Stichting DICA & MRDM. All rights reserved.

## NBCA-R FAIR ##
In this repository we provide the metadata associated with the NBCA-R FAIR dataset (https://fairsharing.org/bsg-s001530/). To access the NBCA-R FAIR data itself, we refer to the standardised procedure for retrieving DICA data. This procedure can be found on the NBCA-R fairsharing page under "Data access" and "Protocol To Gain Access To The Data".

In this repository you can find (1) definitions of the variables that are included in the NBCA-R registry, (2) the R2RML mapping from tabular- to RDF format, (3) a description of- and fairsharing links to the used ontologies and (4) a short description on the process used to convert the tabular NBCA-R data into RDF format. 

### Content dataset ###
In the folder "Content dataset" you can find an Excel file which contains all variables of the NBCA-R registry. In the tab "Alle variabelen" you can find all variables and the corresponding (other) tab of the Excel file where you can find more information about their definitions (columns "Label/Omschrijving" & "Help tekst").

### R2RML mapping ###
In the folder "R2RML mapping" you can find the R2RML mapping file which links the variables of the NBCA-R registry to concepts in the used ontologies (see below). In this folder we also provide visualisations of the R2RML mappings where you can see the ontology concepts and their relations. 

### Used ontologies ###
In the R2RML mapping, NBCA-R registry variables are linked to the ROO ontology, which re-uses NCIT ontology concepts where possible. The version of the ROO ontology that was used for the NBCA-R FAIR pilot is ROO.0.5.owl.

The ROO ontology is developed by MAASTRO clinic to connect existing international terminologies that are focussed on radiotherapy. The fairsharing page of the ROO can be found at https://fairsharing.org/FAIRsharing.3x8jd5 .

The National Cancer Institute Thesaurus (NCIT) ontology is a broad, internationally accepted ontology for biomedical concepts (clinical care, research, etc.). The fairsharing page of the ROO can be found at https://fairsharing.org/bsg-s000096/ .

### Conversion process tabular data to RDF format ###
The NBCA-R data is converted into RDF format in order to adhere to the FAIR principles of interoperability and reusability. Here, variables are linked concepts/relations (and corresponding definitions) in existing ontologies (ROO/NCIT) via URIs. The conversion of tabular data to RDF format is carried out by MRDM using the following open-source software: Protege, db2triples, Python and PostgreSQL. 

The image "Conversion process.png" visualises the conversion process from tabular data to RDF format. From this follows that an R2RML mapping, an R2RML processor and a (relational) database view are required. An R2RML mapping can be seen as the receipt for generating RDF data. Here, variables from the database view are linked to ontology concepts (and corresponding definitions) and relations between concepts are set. In the NBCA-R FAIR pilot, ontology editor Protege has been used to efficiently search existing ontologies for concepts (and corresponding definitions) to link to NBCA-R variables.

MRDM generates the R2RML mapping via a Python script in which concepts and relations, from existing ontologies, are manually linked to NBCA-R variables. Python is a versatile, widely applicable and user-friendly programming language, and consequently one of the most used programming languages to date. Next, the R2RML mapping is executed within the Python script and RDF data is generated. The latter using R2RML processor "db2triples", a Java library which can convert a relational database view, via an R2RML mapping, to RDF format. The database view is realised using PostgreSQL, the worlds most advanced open source relational database. 

### Example RDF data ###
In folder "Example RDF" you can find the file "out.ttl". This file contains fake NBCA-R RDF data for a single patient. This patient has unrealistic values for variables since we wanted to cover as many triples as possible. The example RDF data can be used to draft a SPARQL query for the NBCA-R FAIR dataset.