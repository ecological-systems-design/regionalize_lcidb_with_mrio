Instructions for running the regionalization algorithm
=================

Authors: Sidi Peng, Stephan Pfister<br />
Institution: ETH Zurich; Dept. of Civil, Environmental and Geomatic Engineering; Institute of Environmental Engineering; Ecological Systems Design<br />
Contact: sipeng@ethz.ch

---------------------------
Table of contents

1. General information
2. Version history
3. License 
4. Hardware requirements
5. Software requirements
6. Model structure
7. Obtaining and placing the input data
8. Acknowledgments
9. Welcome contributions

----------------------------

1. General information

This repository contains python codes and parts of input data for generating a regionalized ecoinvent used in the following publication:

Title: A novel approach to regionalizing life cycle inventory with multiregional input-output data: an example of ecoinvent with Exiobase
Authors: Sidi Peng, Stephan Pfister<br />
Year: <br />
Journal: <br />
Issue: N/A<br />
Pages: N/A<br />
Publisher: <br />
Direct link: <br />

The folder "Codes" contains the regionalization algorithm. It includes three subfolders for importing databases, integrating databases, and conduting LCA analysis. The folder "Data" contains some input data and prepared subfolders for output data. <br />
The general status of the model has to be considered "under development" as it runs reliably but it has not been cleaned and improved for ease of access under all potential circumstances.

----------------------------

2. Version history

2023-02-28: Release of version 1.0

Change notes version 1.0: -

----------------------------

3. License 

This repository is released under a BSD 3-Clause "New" or "Revised" License. This licence allows you to share, copy and modify the repository as long as you give credit to the authors. In this specific case, please reference the scientific publication that is the original data source of the repository (-------------). You may not use the repository in a way that suggests the rights holder has endorsed you or your use of the repository. Further permissions are required for the content within the repository that is identified as belonging to a third party.

----------------------------

4. Hardware requirements

Many parts of the algorithm can be run on conventional laptop/ stationary computers within a reasonable time frame. Integrating two databases (2_3_regionalize_ecoinvent_by_iot.ipynb) however requires substantial computational power or a large amount of time. It is therefore strongly recommended to also use server to run this part of the algorithm. These are the specifications of the server that has been used to run the model:

System Manufacturer: FUJITSU<br />
System Model: PRIMERGY RX2540 M4<br />
BIOS: V5.0.0.12 R1.22.0 for D3384-A1x<br />
Processor: Intel(R) Xeon(R) Gold 6154 @ 3.00GHz (72 CPUs)<br />
Memory: 377GiB RAM<br />
Operating System: Ubuntu 18.04.6 LTS<br />

----------------------------

5. Software requirements

The code is written in the programming language Python (Version 3.6.13 from 2021-2-15). The authors used the user-firendly interface of the free software Jupyter Notebook (Version 6.4.3) to write and edit the code. As such, it is necessary to install the Jupyter Notebook interface. The installation details can be found here (https://docs.jupyter.org/en/latest/install/notebook-classic.html). 

Package Brightway2 has to be installed in order to run the code successfully. The introduction and installation of the package can be found here (https://documentation.brightway.dev/en/latest/source/setup/setup.html).

----------------------------

6. Model structure

The general structure of the regionalization algorithm is shown in the publication Figure 1 []. More technical details are introduced in the main notebook, i.e., 2_3_regionalize_ecoinvent_by_iot.ipynb.

----------------------------

7. Obtaining and placing the input data

The input data required to run the full model are listed below. Ecoinvent and Exiobase data need to be obtained and stored in the right format and with the right name in the right folder. The rest data are local, some of which are obtained from online sources and modified mannually regarding the region names.


Input data to be obtained:<br />
(1) ecoinvent 3.7.1_cutoff_ecoSpold02<br />
   - Source: https://ecoinvent.org/the-ecoinvent-database/#, accessed on 17/01/2023, license required<br />
   
(2) exiobase_3_IOT_2011_ixi <br />
   - Source: https://zenodo.org/record/5589597#.Y8YYM3bMJdh, accessed on 17/01/2023, free

Local input data:<br />
(1) eiv3.7_geographies_names_coordinates_shortcuts_overlaps.xlsx<br />
   - Content: It contains list of geographies and intersections in ecoinvent v3.7.1.<br />
   - Source: This version not available from ecoinvent anymore and saved as local file here. The new version can be found from here (https://ecoinvent.org/the-ecoinvent-database/geographies/). <br />
   
(2) country-and-continent-codes-list-added-ME.xlsx <br />
   - Source: https://gist.github.com/stevewithington/20a69c0b6d2ff846ea5d35e5fc47f26c, accessed on 17/01/2023.<br />
   - Modification: We added the missing country - Montenegro into the excel.<br />
   
(3) sector_matching_dicts.pickle<br />
   - Content: This file shows the matching between ecoinvent ISIC codes and exiobase sectors.<br />
   - Source: Jonas Mehr and Simon Roth. Development of a tool refining the regional resolution in life cycle inventory. Project work report, ETH Zürich, 11 2015.
   
(4) AWARE_country_regions_world_april2016_with_modified_region_name.xlsx <br />
   - Source: https://wulca-waterlca.org/aware/download-aware-factors/, accessed on 17/01/2023.<br />
   - Modification: We modified the names of some regions to ensure their names are consistent with the ones in (1).<br />
   
(5) wateruse_elementary_flows_factors.json<br />
   - Content: This files list water use related elementary flows in ecoinvent, which will be assigned with the AWARE CFs.<br />
   - Source: Adrian Haas, Master thesis, July 2016.<br />

----------------------------
8. Acknowledgments
We thank Adrian Haas (former staff in ETH Zurich) very much for his significant contributions to the regionalization algorithm and development of the PyPardiso library for solving large sparse systems of linear equations.

----------------------------

9. Welcome contributions

Even though the model and its outputs have been carefully tested and reviewed, it is possible that it contains errors or could be improved for ease of use and efficiency of calculation. The authors highly value such input and therefore welcome to open issues at github and welcome any bug reports or suggestions that are submitted to sipeng@ethz.ch. In case the model is updated, it will be shown at github under an updated version number. A list of changes between versions will be included in the file "README.md".
