## ATMS-597-SP-2020-Project-3-Group-H
README.md for Project 3 Group H

Group members: Dongwei Fu, Alex Adams,Xinchang Li

========================Project-3-Group-H.py README===============================


This code consists of mainly three parts:
----------------------------------------------------------------------------------
       1. GPCP data downloading and statistics
       2. NCEP Reanalysis data downloading
       3. Plotting NCEP Reanalysis data
----------------------------------------------------------------------------------
       
       
In Part 1, GPCP data downloading is achieved through BeautifulSoup package,
a list of filenames is generated by parsing the html metadata, and each file
follows: download file -> load into xarray -> aggregate -> delete file
sequence to save memory and disk space. 

Once all files have been processed, we end up with the xarray dataset that has
all the days of global precipitation values from 1996.10 to 2019.11, and the 
xarray dataset is then written into netcdf file to store in a local drive. 

We select 'DJF' months by using ```xr.DataArray.sel(time=(mdata['time.season'] == 'DJF'))```
and use ```xr.DataArray.sel(longitude=,latitude=, method='nearest')``` to select
the gridpoint closest to Melbourne, Aus.
We then drop all values that are bad data or fill-values to compute the 95-
percentile precipitation value using ```np.percentile(,95)```.

The Cumulative Probability Distribution Function is plotted using matplotlib.
Finally, the days of precipitation exceeding the 95 percentile threhold is then
written into a new .nc file.

     
      
       


