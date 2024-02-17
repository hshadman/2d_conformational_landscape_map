# Input-Output Guide for the _PyConforMap_ module

**PyConforMap** (**csv_file**, **radius_**= 0.1, **max_x_val**= 3, **max_y_val**= 30, **min_x_val**= 0, **min_y_val**= 0)

PyConforMap is a python class. 

This class generates scatter plots of instantaneous shape ratio (_R<sub>s</sub>_) against relative radius of gyration (_R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_), for a given protein/polymer on top of those of a Gaussian Walk (GW). _R<sub>g</sub><sup>mean</sup>_ is a constant, computed using the entire dataset supplied. 
    
It can be used to examine the scatter plot and analyze metrics. 

Once the dataset is loaded, it prints the % of protein/polymer points that are close to reference (GW) points.

By default, the _GW_chainlen100.csv_ csv file is loaded for use as reference and must be available in the default directory.

### Input Parameters:<br> 

**csv_file** : **_a csv file of shape (n,2)_**<br>
&ensp;&ensp;A csv file containing _R<sub>g</sub><sup>2</sup>_ in the first column and _R<sub>ee</sub><sup>2</sup>_ in the second column. Each row in the file represents a single conformation snapshot.  
**radius_** : **_float, optional_**<br> 
&ensp;&ensp;The radius to use to count GW snapshots that are close to protein/polymer snapshots, or vice versa. Default 0.1. NOTE: All scatter points coordinates are transformed before any such computation is performed.  
**max_x_val** : **_float, optional_**<br>
&ensp;&ensp;maximum x-axis limit for scatter plot. Default 3.  
**max_y_val** : **_float, optional_**<br>
&ensp;&ensp;maximum y-axis limit to use for scatter plot. Default 30.  
**min_x_val** : **_float, optional_**<br>
&ensp;&ensp;minimum x-axis limit for scatter plot. Default 0.  
**min_y_val** : **_float, optional_**<br>
&ensp;&ensp;minimum y-axis limit to use for scatter plot. Default 0.  

## Methods:

<details>

<summary>plot_protein_against_GW - generates the scatter plot</summary>

**PyConforMap.`plot_protein_against_GW`** (**protein_label**, **provided_color**= 'magenta')


This method generates a scatter plot of instantaneous shape ratio (_R<sub>s</sub>_) against relative radius of gyration (_R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_) for both a protein/polymer and GW. GW points are shown in black by default.

Input Parameters:<br> 

**protein_label** : **_string_**<br>
&ensp;&ensp;A string to identify the protein points on the scatter plot.  
**provided_color** : **_string, optional_**<br>
&ensp;&ensp;The color of the provided protein/polymer points. Default magenta.

An attribute _fC_value_, containing _f<sub>C</sub>_, is assigned once this method is run.

</details>

<details>

<summary>check_boundary - computes % of protein/polymer points within the pre-assigned radius of GW points</summary>

**PyConforMap._check_boundary_** ()

This method prints out what % of protein/polymer points are within the pre-provided radius of at least one GW points on the scatter plot. To enable this computation, the coordinates of all points on the scatter plot are temporarily transformed (occurs completely in the background), as _R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_ and _R<sub>s</sub>_ have different ranges.

</details>