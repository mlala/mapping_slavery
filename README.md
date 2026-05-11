# Mapping Slavery - a paved legacy in Brooklyn
A prototype for GIS data visualization

## Project Description
This project is built to visualize the streets in Brooklyn that are named after enslaver families. For the prototype, the focus is on the neighborhood of Flatbush which was previously a town in the 18th and 19th centuries. The streets highlighted identify slave-holding families and list the names of the enslaved held captive by the family. The charts extrapolate data from the North East Slavery Records Index to show the amount of people enslaved according to records of the time, broken down by family and year.

## Motivation

The history of African enslavement in the United States focuses heavily on the South, where slavery lasted the longest. However, Northern states and territories were also involved in the slave trade from the beginning, even though their role is downplayed due to earlier abolition. Wall Street was one of early America's top slave auction blocks. In a previous class, I learned more about Seneca Village, a settlement of free African Americans that was expelled to create Central Park.I learned a few years back that Cortelyou Rd in Brooklyn was named after an enslaver, and that stuck with me. Despite the abolitionist sentiment of the North, there are countless reminders of slavery's legacy in New York City.  For this project I wanted to see if there were any other street names with the similar history. I looked up old maps in the digital collections of the New York Public Library to investigate evidence of plantations, and I found a map from 1855, ["Plan of the city of Brooklyn, L.I."](https://digitalcollections.nypl.org/items/81e4f3e0-c5aa-012f-109b-58d385a7bc34). This map showed old farm lines with the corresponding property owners, as well as planned streets and street names. I saw a lot of familiar names on this map and decided to look further. This led me to finding enslavement information from The Journal of Slavery and Data Preservation, the NYC Municipal Archives, [In Pursuit of Freedom](https://pursuitoffreedom.org/) and the [North East Slavery Records Index](https://nesri.commons.gc.cuny.edu/). I confirmed a lot of the connections I made from the old city maps and decided to move ahead with this project. I feel very strongly that knowing the past informs the present and shapes the future. If we can make the connections to our history, we can remedy those old mistakes and educate New Yorkers about the violence that built this city.

## Workflow

I worked with Python and several Python libraries to clean, analyze, and visualize the data. In Jupyter Lab I imported and installed Folium, GeoPandas, and PyGris for GIS spatial data, Pandas and Matplotlib for data analysis and chart visualization. I also referenced two key courses from O'Reilly to educate myself on Python. I'd like to take a moment to thank Fred Benton, co-director of NESRI for the Brooklyn dataset and the Brooklyn directory of families. 

### Data Clean Up

Most of the clean up happened after importing the NESRI csv. I made sure to convert year columns into datetime format and delete all erroneous columns and rows. This reduced the size of the object and made it easier to work with for creating dataframes.

### DataFrames
Most of the work was done by creating various dataframes in Pandas and GeoPandas. I created two separate geodataframes by geocoding the neighborhood of Flatbush and the selected streets to have the geometry (lat and lon points) for plotting on a map, which could be exported as an html file and embedded in a static site. I used PyGris for the street geocoding, although it is a small library, because it simplifies the Census API and it allows users to isolate local roads as polylines. I used GeoPandas to create these geodataframes because it is integrated with Folium. It enables me to align these points onto a map and add pop ups and markers with geojson language. After I made the geodataframes, I made other dataframes based on the family data. I created one df for each chart that I would plot. This kept the data a bit more tidy and avoided accidentally modifying the wrong dataframe. 

### Mapping

After the dataframes and geodataframes were created, I used mainly Folium and Matplotlib to visualize them. It is my first time manipulating GIS data and Folium is very user friendly, opposed to arcGIS which is an industry-wide standard but has a steeper learning curve. If anyone would like to use that instead, I'm sure the same results can be reproduced with a basemap, tileset, and polygon layers. 

## Future Use

I hope that I can keep working on this project and map the entirety of Brooklyn. I'd like to work with NESRI directly to accomplish this. Also, the street names must be investigated using genealogical records. Some family names were spelled mutliple ways, like the Vanderveers, and it is unclear at this moment if these were different families or misspellings. This would be done outside of a Python environment and requires dedicated archival research. Additionally, someone could digitze the old Brooklyn planning map and make an interactive layer that highlights property ownership before modern Brooklyn. I imagine a team of GIS and data visualization professionals and geographical librarians could tackle that. There are a lot of exciting paths from this project.

## Files List

* [Interactive map](/finalmap_refd.html) - final_maprefd

  #### Charts made of family enslavement totals

  * All families data -  [families_bar](/families_bar.html) and families_bar.json
  * Clarkson - [clarkson_table.html](clarkson_table.html) and clarkson_table_plain.json
  * Cortelyou - [cortelyou_table.html](cortelyou_table.html) and cortelyou_table_plain.json
  * Ditmas - [ditmas_table.html](ditmas_table.html) and ditmas_sum_table.json
  * Lefferts - [lefferts_line.html](/lefferts_line.html) and lefferts_line.json
  * Lott - [lott_line.html](/lott_line.html) and lott_line.json
  * Martense - [martense_line.html](/martense_line.html) and martense_line.json
  * Remsen - [remsen_line.html](/remsen_line.html) and remsen_line.json
  * Vanderveer - [vanderveer_line.html](/vanderveer_line.html) and vanderveer_line.json

* GeoJSON file with neighborhood geometry - boroquery.json
