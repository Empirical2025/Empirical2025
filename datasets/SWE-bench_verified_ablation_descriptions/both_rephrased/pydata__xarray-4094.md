to_unstacked_dataset broken for single-dim variables  
<!-- A short summary of the issue, if appropriate -->

#### MCVE Code Sample
To reproduce the issue, create a one-dimensional data array of length three with values 0, 1, and 2 indexed by a coordinate named “x.” Next, assemble a dataset containing two variables, “a” and “b,” both based on that same array. Apply a stacking operation that collapses the “x” dimension into a new combined dimension called “y.” Finally, attempt to unstack the dataset along “y.”

When you run the unstack operation, a merge conflict error occurs because the two variables both define values for the “y” coordinate in a way that cannot be reconciled.

#### Expected Output
A working roundtrip.

#### Problem Description
I need to stack a bunch of variables and later unstack them again, however this doesn't work if the variables only have a single dimension.

#### Versions

<details><summary>Output of <tt>xr.show_versions()</tt></summary>

INSTALLED VERSIONS
------------------
commit: None
python: 3.7.3 (default, Mar 27 2019, 22:11:17) 
[GCC 7.3.0]
python-bits: 64
OS: Linux
OS-release: 4.15.0-96-generic
machine: x86_64
processor: x86_64
byteorder: little
LC_ALL: None
LANG: en_GB.UTF-8
LOCALE: en_GB.UTF-8
libhdf5: 1.10.4
libnetcdf: 4.6.2

xarray: 0.15.1
pandas: 1.0.3
numpy: 1.17.3
scipy: 1.3.1
netCDF4: 1.4.2
pydap: None
h5netcdf: None
h5py: 2.10.0
Nio: None
zarr: None
cftime: 1.0.4.2
nc_time_axis: None
PseudoNetCDF: None
rasterio: None
cfgrib: None
iris: None
bottleneck: None
dask: 2.10.1
distributed: 2.10.0
matplotlib: 3.1.1
cartopy: None
seaborn: 0.10.0
numbagg: None
setuptools: 41.0.0
pip: 19.0.3
conda: 4.8.3
pytest: 5.3.5
IPython: 7.9.0
sphinx: None

</details>