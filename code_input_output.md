# Input-Output Guide for the _PyConforMap_ module

**PyConforMap** (**csv_file**, **radius_**= 0.1, **max_x_val**= 3, **max_y_val**= 30, **min_x_val**= 0, **min_y_val**= 0)

PyConforMap is a python class. 

This class generates scatter plots of instantaneous shape ratio (_R<sub>s</sub>_) against relative radius of gyration (_R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_) for a protein or polymer against those of Gaussian Walk (GW) polymer model reference. _R<sub>g</sub><sup>mean</sup>_ is a constant, computed using the entire dataset supplied. 
    
It can be used to examine the scatter plot and analyze metrics. 

Parameters:<br> 
**csv_file** : **_a csv file of shape (n,2)_**  
&ensp;A csv file containing _R<sub>g</sub><sup>2</sup>_ in the first column and _R<sub>ee</sub><sup>2</sup>_ in the second column. Each row in the file represents a single conformation snapshot.  
**radius_** : **_float, optional_**
&ensp;&ensp;The radius to use to count GW snapshots that are close to protein/polymer snapshots, or vice versa. Default 0.1. NOTE: All scatter points coordinates are transformed before any such computation is performed.  
**max_x_val** : **_float, optional_** 
&ensp;&ensp;maximum x-axis limit for scatter plot. Default 3.  
**max_y_val** : **_float, optional_**
&ensp;&ensp;maximum y-axis limit to use for scatter plot. Default 30.  
**min_x_val** : **_float, optional_** 
&ensp;&ensp;minimum x-axis limit for scatter plot. Default 0.  
**min_y_val** : **_float, optional_**
&ensp;&ensp;minimum y-axis limit to use for scatter plot. Default 0.  
