# Technical Details for the _PyConforMap_ python module
### _class_ PyConforMap  **csv_file**, **radius_**= 0.1, **max_x_val**= 3, **max_y_val**= 30, **min_x_val**= 0, **min_y_val**= 0

module to generate scatter plots of instantaneous shape ratio (_R<sub>s</sub>_) against relative radius of gyration (_R<sub>g</sub>/R<sub>g</sub><sup>mean</sup>_) for a protein or polymer against those of Gaussian Walk (GW) polymer model reference. 
    
This class can be used to examine the scatter plot and analyze metrics. 

Input parameters: **csv_file**, **radius_**= 0.1, **max_x_val**= 3, **max_y_val**= 30, **min_x_val**= 0, **min_y_val**= 0

Parameters: **csv_file** : **_a csv file of shape (n,2)_** 
- A csv file containing _R<sub>g</sub><sup>2</sup>_ in the first column and _R<sub>ee</sub><sup>2</sup>_ in the second column. Each row in the file represents a single conformation snapshot. 