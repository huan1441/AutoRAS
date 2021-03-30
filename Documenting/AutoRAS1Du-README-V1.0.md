# AutoRAS1Du
AutoRAS1Du is a Python module, which is created based on the HEC-RAS API (RAS507.HECRASController and RAS507.HECRASGeometry), includes several functions that can automate a HEC-RAS 1D unsteady flow simulation:
1) Py2HecRas_1DU_Flow(): create a 1D unsteady flow data file based on the given HEC-RAS geometry data and boundary data (upstream streamflow data and downstream friction slope which are stored in separate CSV files for each reach);
2) Py2HecRas_1DU_Geo(): modify the Manning's n (given multiply factor) in the original geometry file and create a new geometry file with new Manning's n;
3) Py2HecRas_1DU_Plan(): create a HEC-RAS 1D unsteady flow plan file based on a template list in the script;
4) Py2HecRas_1DU_Project(): modify the original HEC-RAS project file;
5) Py2HecRas_1DU_Run(): run HEC-RAS 1D unsteady flow analysis and extract unsteady results (WSE, flow, average velocity of flow in main channel, and average velocity of flow in total cross section) from the HEC-RAS HDF file, and save as separate CSV files.


## Installation
The appropriate version of HEC-RAS must already be installed to use rascontrol.

    c:\> git clone https://github.com/AutoRAS
    
    c:\> cd AutoRAS
    
    c:\AutoRAS> pip install .

## Basic Usage
```python
>>> import AutoRAS1Du

>>> # Create a 1D unsteady flow data file based on given boundary data
>>> Py2HecRas_1DU_Flow(ProjectName="WabashAndTributarie")

>>> # Create a HEC-RAS 1D unsteady flow plan file
>>> Py2HecRas_1DU_Plan(g=1,u=1,
                       StartDateTime="2008-01-21 00:00",
                       EndDateTime="2008-02-21 00:00",
                       ProjectName="WabashAndTributarie")

>>> # Run HEC-RAS 1D unsteady flow analysis and get results (WSE, flow, velocity)
>>> Py2HecRas_1DU_Run(ProjectName="WabashAndTributarie")    

```
## Notes Before Using
1) Name the boundary data files (CSV): ¡°BC_RiverID_ReachID".csv in the Folder "1D_Unsteady_BC".
2) Results named as "Variable of ProjectName".csv are stored in the Folder "1D_Unsteady_Results" 