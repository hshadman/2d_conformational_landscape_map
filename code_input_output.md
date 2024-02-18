# Input-Output Guide for the _PyConforMap_ module

**PyConforMap** (**csv_file**, **radius_**= 0.1, **max_x_val**= 3, **max_y_val**= 30, **min_x_val**= 0, **min_y_val**= 0)

PyConforMap is a python class. 

This class generates scatter plots of instantaneous shape ratio (_R<sub>s</sub>_) against relative radius of gyration (_R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_), for a given protein/polymer simulation on top of those of a Gaussian Walk (GW) simulation. _R<sub>g</sub><sup>mean</sup>_ is a constant, computed using the entire dataset supplied. 

The model requires the _pandas_, _numpy_, _matplotlib_, _scipy_, _itertools_, _more_itertools_ and _random_ python packages.  

**THE MODULE CODE REQUIRES ONE INPUT FILE:** It is a csv file (for a given protein/polymer simulation) with 2 columns. The first column contains _R<sub>g</sub><sup>2</sup>_ values and the second column contains _R<sub>ee</sub><sup>2</sup>_ values. In this (user provided) file, each row (effectively) represents a protein/polymer conformation snapshot from the simulation. An example input is the 'example_protein.csv' csv file (included with repository). A second csv file, for the reference (GW) simulation, is already included with this repository.  
    
It can be used to examine the scatter plot and analyze metrics. 

Once the dataset is loaded, it prints the % of protein/polymer points that are close to reference (GW) points.

By default, the _GW_chainlen100.csv_ csv file is loaded for use as reference and must be available in the default directory.

### Input Parameters:<br> 

**csv_file** : **_a csv file of shape (n,2)_**<br>
&ensp;&ensp;A csv file containing square of the radius of gyration (_R<sub>g</sub><sup>2</sup>_) in the first column and square of the end-to-end distance (_R<sub>ee</sub><sup>2</sup>_) in the second column. Each row in the file represents a single conformation snapshot for a protein/polymer.  
**radius_** : **_float, optional_**<br> 
&ensp;&ensp;The radius to use to count GW snapshots that are close to at least one protein/polymer snapshot, or vice versa. Default 0.1.  
&ensp;&ensp;**NOTE**: All scatter point coordinates are transformed before any such counting is performed.  
**max_x_val** : **_float, optional_**<br>
&ensp;&ensp;maximum x-axis limit for scatter plot. Default 3.  
**max_y_val** : **_float, optional_**<br>
&ensp;&ensp;maximum y-axis limit to use for scatter plot. Default 30.  
**min_x_val** : **_float, optional_**<br>
&ensp;&ensp;minimum x-axis limit for scatter plot. Default 0.  
**min_y_val** : **_float, optional_**<br>
&ensp;&ensp;minimum y-axis limit to use for scatter plot. Default 0.  

## Methods:

### Click to Expand
<details>

<summary>plot_protein_against_GW - generates the 2D scatter plot</summary>

**PyConforMap.`plot_protein_against_GW`** (**protein_label**, **provided_color**= 'magenta')


This method generates a scatter plot of instantaneous shape ratio (_R<sub>s</sub>_) against relative radius of gyration (_R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_) for both a protein/polymer and GW. GW points are shown in black by default. If any data point exceeds a default axis limit, axis limit will be automatically readjusted. 

### Input Parameters:<br> 

**protein_label** : **_string_**<br>
&ensp;&ensp;A string to identify the protein points on the scatter plot.  
**provided_color** : **_string, optional_**<br>
&ensp;&ensp;The color of the provided protein/polymer points. Default magenta.

An attribute _fC_value_, containing _f<sub>C</sub>_, is assigned once this method is run.

</details>

<details>

<summary>check_boundary - computes % of protein/polymer points within the pre-assigned radius of GW points</summary>

**PyConforMap.`check_boundary`** ()

This method prints out what % of protein/polymer points are within the pre-provided radius of at least one GW points on the scatter plot. To enable this computation, the coordinates of all points on the scatter plot are temporarily transformed (occurs completely in the background), as _R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_ and _R<sub>s</sub>_ have different ranges.

</details>

<details>

<summary>change_xlim_ylim - update x-axis and y-axis limits</summary>

**PyConforMap.`change_xlim_ylim`** (**min_x_val**, **min_y_val**, **max_x_val**, **max_y_val**) 

Updates x-axis and y-axis limits of scatter plot. 

### Input Parameters:<br> 

**min_x_val** : **_float_**<br>
&ensp;&ensp;Desired minimum x-axis limit.  
**min_y_val** : **_float_**<br>
&ensp;&ensp;Desired minimum y-axis limit.  
**max_x_val** : **_float_**<br>
&ensp;&ensp;Desired maximum x-axis limit.  
**max_y_val** : **_float_**<br>
&ensp;&ensp;Desired maximum y-axis limit.  

</details>

<details>

<summary>vary_protein - plot f<sub>C</sub> against protein/polymer snapshots</summary>

**PyConforMap.`vary_protein`** (**protein_lab**, **no_dots** = 20) 

Generates a plot of _f<sub>C</sub>_ against number of protein/polymer snapshots.

### Input Parameters:<br> 

**protein_lab** : **_string_**<br>
&ensp;&ensp;A string to identify the protein  
**no_dots** : **_int_**<br>
&ensp;&ensp;The number of data points to show on the plot. Default 20. E.g. if simulation has 200,000 snapshots, the x-axis will plot 10,000, 20,000 ... 200,000 and the y-axis will show _f<sub>C</sub>_ at each of those snapshot counts, if no_dots = 20.

</details>

<details>

<summary>vary_GW_ref - plot f<sub>C</sub> against GW snapshots</summary>

**PyConforMap.`vary_GW_ref`** (**protein_lab**, **no_dots** = 40) 

Generates a plot of _f<sub>C</sub>_ against number of GW snapshots.  

### Input Parameters:<br> 

**protein_lab** : **_string_**<br>
&ensp;&ensp;A string to identify the protein  
**no_dots** : **_int_**<br>
&ensp;&ensp;The number of data points to show on the plot. Default 40. E.g. if simulation has 720,000 snapshots, the x-axis will plot 18,000, 36,000 ... 720,000 and the y-axis will show _f<sub>C</sub>_ at each of those GW snapshot counts, if no_dots = 40.

</details>

<details>

<summary>regenerate_GW_chain - simulates new GW reference chain</summary>

**PyConforMap.`regenerate_GW_chain`** (**chain_length**, **nosnaps**, **interval**= 1, **mu**= 0, **sigma**= 1)

This method simulates an entirely new GW chain to be used as a reference. The simulation is such that each snapshot consists of a polymer chain conformation where the distance of one monomer to the next was randomly selected from a gaussian distribution with mean 0 and standard deviation 1. Also saves this simulation as the current reference GW simulation, replacing the default. 

Returns a pandas dataframe of shape (n,2) of chain quantities at each snapshot (row represents snapshot), first column is _R<sub>g</sub><sup>2</sup>_ and second column is _R<sub>ee</sub><sup>2</sup>_. n is the number of snapshots. 

### Input Parameters:<br> 

**chain_length** : **_int_**<br>
&ensp;&ensp;The desired number of monomers of the chain.  
**nosnaps** : **_int_**<br>
&ensp;&ensp;The desired number of snapshots in the simulation. Each snapshot is a new randomly generated chain conformation.  
**interval** : **_int, optional_**<br>
&ensp;&ensp;The number of simulation steps to go through in-between snapshots. Default 1.  
**mu** : **_float, optional_**<br>
&ensp;&ensp;The mean of the gaussian distribution from which to randomly select distance of one monomer to next. Default 0.  
**sigma** : **_float, optional_**<br>
&ensp;&ensp;The standard deviation of the gaussian distribution from which to randomly select distance of one monomer to next. Default 1.  

### Returns:<br> 

A pandas dataframe of the new GW simulation. 

</details>

<details>

<summary>save_GW_chain_to_csv - save current GW chain data to a csv file</summary>

**PyConforMap.`save_GW_chain_to_csv`** (**direc** = './')

Saves the current GW reference chain simulation to a csv file. The filename is _GW_chainlenZ_Y_snapshots.csv_ where _Z_ and _Y_ are the chain length and number of snapshots respectively. 

**direc** : **_string, optional_**<br>
&ensp;&ensp;The directory in which to save the file. Default './'.  
</details>

<details>

<summary>retrieve_default_GW_chain - revert to default reference simulation</summary>

**PyConforMap.`retrieve_default_GW_chain`** ()

Revert to the default GW reference simulation. Re-loads the _GW_chainlen100.csv_ csv file to use as reference. 

</details>

## Attributes:<br> 

**protein_rg2** : **_array_**<br>
&ensp;&ensp;A numpy array of the square of the protein/polymer radius of gyration values.

**protein_ree2** : **_array_**<br>
&ensp;&ensp;A numpy array of the square of the protein/polymer end-to-end distance values.

**protein_rg_mean** : **_float_**<br>
&ensp;&ensp;The mean of the protein/polymer radius of gyration, computed from all data combined.

**GW_df** : **_pandas dataframe_**<br>
&ensp;&ensp;A dataframe of the GW reference simulation, which by default is the provided _GW_chainlen100.csv_ file. The columns, in order, are GW chain length, square of radius of gyration, square of end-to-end distance, relative radius of gyration, and instantaneous shape ratio. Each row represents a conformation snapshot from the GW simulation.  