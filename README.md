# PLEASE READ FIRST

## Introducing PyConforMap: Draw pretty maps of your polymer or disordered protein conformational ensembles!

## This repository provides a easy-to-implement python module called _PyConforMap_ that generates scatter plots of instantaneous shape ratio (_R<sub>s</sub>_) against relative radius of gyration (_R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_).

### This is release 1.0.0. This is the initial release. 

### HOW TO CITE: If you use this module, please cite us using the doi: 

The _R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_ is a measure of (relative) size for a protein or polymer chain, and _R<sub>s</sub>_ is a measure of its shape. _R<sub>s</sub>_ is expected to be low (~2 or lower) for compact structures and high for highly extended structures (~12 or higher). An (_R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_, _R<sub>s</sub>_) value constitutes an entity's instantaneous conformation. All (_R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_, _R<sub>s</sub>_) values, when plotted together, constitute a map of the conformational landscape of the entity. 

This module generates (_R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_, _R<sub>s</sub>_) scatter plots of a protein/polymer (data provided by user) against that of a Gausssian Walk (GW) polymer chain model (data for 720000 snapshots of a GW model of length 100 included with repository). The included GW file is 'GW_chainlen100.csv.' The python module can be additionally used to generate a new GW file with different features, should the user wish to do so.

The input needed from the user for the module is a csv file with 2 columns, the first column being _R<sub>g</sub><sup>2</sup>_ values with the second column containing the corresponding _R<sub>ee</sub><sup>2</sup>_ values. An example input it the 'example_protein.csv' csv file (included with repository).  

The 'documentation.md' file provides all technical details of the module. The '2d_conformation_map.ipynb' jupyter notebook file contains the python module code along with examples to illustrate implementation of the code. 

