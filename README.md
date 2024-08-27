# auto_web_maps
## Automate the creation of web maps from GeoParquet files using Python and Folium in a Jupyter Notebook.

This project automates the generation of interactive web maps using spatial data from watershed and stream files in Parquet format. The maps highlight Texas watersheds and drainage networks, providing search functionality, tooltips, pop-ups, and custom styling for both named and unnamed streams. The project utilizes Python, Folium, and GeoPandas for data manipulation and web map generation. The plugin selection and styling of the webmap are placeholders for demonstration purposes.

## Note about the input data
The watershed polygons and streams were extracted from the National Hydrography dataset for the state of Texas. I used python and geopandas to get the dataset, transform the features, create geoparquet files for individual watersheds, and create individual geoparquet files with the streams for each watershed.
The streams table for this dataset contains just over 2 million rows and includes a geometry column. I wanted to break the strean data into smaller pieces based on an appropriate extent such as the level 8 watersheds to reduce resource requirements and increase analysis speed. I also wanted to convert the data to a more performant file format that could be efficiently queried, transported, and stored. 

## Functions
There are four functions used to create the parquet files to interactive web maps.
### extract_common_number(filename)
- Extracts an 8-digit hydrologic unit code (HUC) from file names to match corresponding watershed and stream files.
### add_banner_to_html(output_html, title)
- Adds a customizable banner to the top of the web map HTML file, providing file-specific watershed information.
### create_webmap(gdf_ws, gdf_strm, output_html, title)
- Generates a Folium web map centered on Texas with various interactive elements such as tooltips, popups, legends, and search functionality. The map displays watersheds and streams with different styling and allows for user interaction.
### process_parquet_files(folder_path_ws, folder_path_strm, output_folder)
- Reads watershed and stream Parquet files, matches them based on HUC, and automatically generates web maps for each pair of matching files. Outputs the maps as HTML files.
