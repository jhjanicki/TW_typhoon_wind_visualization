# Visualize wind speed

## Process
1. Load in necessary libraries
2. Load in netcdf file using the netCDF4 library
3. Get the u_wind and v_wind variables: dataset.variables['u'][:], dataset.variables['v'][:]
4. calculate the wind speed: wind_speed = np.sqrt(u_wind**2 + v_wind**2)
5. Get the lats and lons: dataset.variables['latitude'][:], dataset.variables['longitude'][:]
6. Create color maps: i.e. my_cmap = plt.colormaps['twilight']
7. Use maplotlib to plot contours: plt.contourf(lons, lats, wind_speed, 60, transform=ccrs.PlateCarree())
8. IF don't want a global map, set the extent like this: ax.set_extent([118, 130, 15, 35], crs=ccrs.PlateCarree())
9. Add arrows using on top of map using maplotlib quiver: plt.quiver(lons, lats, u_wind, v_wind, scale=800, color='k')

## Data
NOAA
- NOMADS Data at NCEP: https://nomads.ncep.noaa.gov/
1. Parameters: GFS sflux, UGRID, VGRID, 1 hybrid level
2. We will get a GRIB file, will need to convert it to a .nc file 

Some other wind sources: 
- NCEI GFS: https://www.ncei.noaa.gov/products/weather-climate-models/global-forecast
- Copernicus: https://cds.climate.copernicus.eu/cdsapp#!/dataset/reanalysis-era5-single-levels?tab=form


## Some example outputs (testing different colors)
Global map

<img width="800" alt="Screenshot 2023-07-12 at 15 21 04" src="https://github.com/jhjanicki/process_wind_data/assets/6565011/c751b698-d351-4b6c-87f4-a2e74687f989">

Global map with Robinson projection

<img width="800" alt="Screenshot 2023-07-12 at 15 24 01" src="https://github.com/jhjanicki/process_wind_data/assets/6565011/e70991f9-89c6-47bd-9918-e9ade85c2de5">

Map zoomed into Taiwan

<img width="400" alt="Screenshot 2023-07-12 at 15 15 23" src="https://github.com/jhjanicki/process_wind_data/assets/6565011/7f4a575f-cdb3-43f7-98ab-2468f0da0e39">
