# Visualize wind speed, focus on typhoon in Taiwan

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
- NOMADS Data at NCEP: https://nomads.ncep.noaa.gov/gribfilter.php?ds=gfs_sflux
1. Parameters: GFS sflux, UGRID, VGRID, 1 hybrid level
2. We will get a GRIB file, will need to convert it to a .nc file 

Some other wind sources: 
- NCEI GFS: https://www.ncei.noaa.gov/products/weather-climate-models/global-forecast
- Copernicus: https://cds.climate.copernicus.eu/cdsapp#!/dataset/reanalysis-era5-single-levels?tab=form


## Some example outputs (testing different colors)
Global map
<img width="800" alt="Screenshot 2023-07-10 at 15 06 33" src="https://github.com/jhjanicki/TW_typhoon_wind_visualization/assets/6565011/45c86442-b80f-4ed3-98c0-e8eb66396ee0">

Global map with Robinson projection

<img width="800" alt="Screenshot 2023-07-13 at 15 56 25" src="https://github.com/jhjanicki/TW_typhoon_wind_visualization/assets/6565011/37566b7b-f8b3-4a30-bee3-8d20822b32c2">

Map zoomed into Taiwan

<img width="400" alt="Screenshot 2023-07-13 at 15 56 38" src="https://github.com/jhjanicki/TW_typhoon_wind_visualization/assets/6565011/59e055a0-8157-46d9-b1ee-38337c83c2c6">


