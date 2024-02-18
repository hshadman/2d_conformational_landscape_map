# _PyConforMap_: Draw pretty maps of your polymer or disordered protein conformational ensembles!

## PLEASE READ FIRST

## This repository provides an easy-to-implement python module called _PyConforMap_ that generates scatter plots of instantaneous shape ratio (_R<sub>s</sub>_) against relative radius of gyration (_R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_).

### If you have comments/suggestions, please feel free to email me at hs4md@virginia.edu.

### HOW TO CITE: If you use this module, please cite us using the provided doi. 

The _R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_ is a measure of (relative) size for a protein or polymer chain, and _R<sub>s</sub>_ is a measure of its shape. _R<sub>s</sub>_ is expected to be low (~2 or lower) for compact structures and high for highly extended structures (~12 or higher). A single _R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_ value and corresponding _R<sub>s</sub>_ value for a polymer together constitute its instantaneous conformation. When all the _R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_ and  _R<sub>s</sub>_ values of a polymer are plotted together, they constitute what we call a 2D map of the conformational landscape of that polymer.

This module generates 2D scatter plots of _R<sub>s</sub>_ against _R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_ for a protein/polymer (data and protein label/identity provided by user) and a Gausssian Walk (GW) polymer chain model (data for 720000 snapshots of a GW model of length 100 included with repository). Each point on the scatter plot (belonging to either GW or a given protein/polymer) represents a conformation snapshot, and has coordinates (_R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_, _R<sub>s</sub>_). The GW model is intended to be a reference model, whose conformational landscape map (i.e. as represented by all the (_R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_, _R<sub>s</sub>_) points) serves as a 'universal' or reference map for those of other proteins/polymers. Along with the 2D scatter plot, an _f<sub>C</sub>_, representing the fraction of the GW points 'close' (i.e. within a pre-defined boundary) to the protein/polymer points, is automatically calculated. The included GW file is 'GW_chainlen100.csv.' The python module can be additionally used to generate a new GW file with different features, should the user wish to do so.

**THE MODULE CODE REQUIRES ONE INPUT FILE:** It is a csv file (for a given protein/polymer simulation) with 2 columns, the first column being _R<sub>g</sub><sup>2</sup>_ values with the second column containing the _R<sub>ee</sub><sup>2</sup>_ values. An example input is the 'example_protein.csv' csv file (included with repository).In this file, each row represents a protein/polymer conformation snapshot from the simulation, and it is provided by the user. A second csv file, for the reference (GW) simulation, is already provided with this repository.  

The 'code_input_output.md' file provides technical details (input arguments, expected outputs) of the module. The 'pyconformap.py' file contains the source code for the module.  The 'illustrated_example.ipynb' jupyter notebook file shows examples to illustrate implementation of the code. 

_PyConforMap_ is a companion to a paper that is under review for publication, as of 15 Feb, 2024. 