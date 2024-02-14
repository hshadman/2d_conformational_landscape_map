# PLEASE READ FIRST

## This repository provides a easy-to-implement python module called _display_2d_map_ that generates scatter plots of instantaneous shape ratio (_R<sub>s</sub>_) against relative radius of gyration (_R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_).

### This is release 1.0.0. This is the initial release. 

### HOW TO CITE: If you use this module, please cite us using the doi: 

An _R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_ and _R<sub>s</sub>_ value constitute an entity's instantaneous conformation. All _R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_ and _R<sub>s</sub>_ values, when plotted together, constitute a map of the conformational landscape of the entity. 

The module generates scatter plots of the conformational landscape of a protein/polymer (data provided by user) against that of a Gausssian Walk (GW) polymer chain model (data for 720000 snapshots of a GW model of length 100 included with repository). The included GW file is GW_chainlen100.csv. The python module can be additionally used to generate a new GW file with different features, should the user wish to do so.

The python module input needed from the user is a csv file with 2 columns, the first column being _R<sub>g</sub><sup>2</sup>_ values with the second column containing the corresponding _R<sub>ee</sub><sup>2</sup>_ values. 

The 'documentation' file provides further  technical details for the python module. The '2d_conformation_map.ipynb' jupyter notebook file contains the python module code along with demonstrated examples. A csv file 'example_protein.csv' is provided to illustrate a few example implementations of the python module. 

