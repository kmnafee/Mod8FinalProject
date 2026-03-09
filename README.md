# Mod8FinalProject
The repository is created for the final Project for MAP 673 course

# Urban Tree Phenophase Explorer

GitHub Pages
https://kmnafee.github.io/Mod8FinalProject/

GitHub repository:

https://github.com/kmnafee/Mod8FinalProject


he purpose of the project is to develop an interactive webmap that explores the phenophase of different trees across the UKY campus at species-level. It allows the user to view different phenophase of individual trees across multiple years. Phenophases are the different stages of biological events in a plant's life cycle such as greenip, sensescence, dormancy, maturity etc. The user can gain insight about the timing of these different stages across multiple years of more than 2600 trees.

## Data Source

The datasets include
 ### 1) UK Tree Inventory Data
 The spatial dataset contains the approximate canopy extent for these individual trees across the campus. The base dataset was collected from the UK Facilities and Management department and then later refined and converted into polygon data by using Arc GIS pro

 ### 2) Phenophase Data
 The phenophase were calculated using time-series NDVI data derived from PlanetScope imagwes. These represent key transition in tree canopy development. Six phenophase were calculated in this study. These are

 #### Greenup onset
 #### Mid Greenup
 #### Maturity
 #### Senescence onset
 #### Mid Senescence 
 #### Dormancy

 These datasets are included in the repository under the Data folder.

## Methodology

The project workflow involved several steps integrating geospatial data processing and web mapping technologies. There was a lot of steps that went into preparing these two datasets which I did during my analysis for my ongoing thesis work. For this final project,

First, the UK tree inventory dataset was converted into spatial polygons representing approximate canopy extents. The phenophase dataset was stored as a tabular CSV file containing phenological metrics for each tree across multiple years. A unique identifier called TARGET_FID  was used to join the spatial dataset and the phenophase dataset. This allowed each tree polygon to be associated with its corresponding phenological values.The joined dataset was then visualized in an interactive web map where users can explore individual trees, view phenophase information, and filter species across different years.  



 ## Representation
 The map represents indivdual trees as color-coded polygon. Each tree is colored based on the species name derived from the inventory dataset. The legend shows all species and their corresponding color. The map has some interactive popups that allows the user to see the Tree Name, Tree ID (TARGET_FID) and the Phenophases for the selected year. Additional UI controls were added to the map that allows the user to toggle between the years and filter the trees by species name.

 ## UI Design
The interactive map follows a three column layout. The central panel includes the main map displaying the color coded polygons across the study area. The left panel contains the year toggle control, species filter and the legend. The right panel displays the information of the trees when the user clicks on a specific tree polygon. For the title display, the map uses a Playfair Display font and for the interface text it uses Inter font.

## Map Objective 

The objective of the map is to present the phenological data in an interactive format for broader audience. Though these type of data are mainly presented in scientific articles, rarely they are presented in an interactive way. Thus the main purpose of this is to show how hard scientific data can be presented in an interactive manner for the broader audience.

## Technology Stack

The project was developed using a combination of web mapping and JavaScript libraries. These were

### HTML

### CSS

### JavaScript

### Leaflet.js for interactive web mapping

### Bootstrap for user interface components

### PapaParse for parsing CSV phenophase data

### shp.js for loading shapefile data in the browser

### GitHub Pages for web hosting

## Description of the Final Version

The final version was created using single index html file. This integrates all the required libraries and the functions needed to load the spatial and the tabular datasets. The core logic of the application is implemented through several JavaScript functions within the index html file. The map was centerred on the UK campus and the dark CARTO was used as the basemap. The csv/tabular data which was the phenophase dataset was loaded using Papa Parse function. The shapefile zip was loaded using the shp.js function. JoinData () was used to join the shapefile and the CSV using the common TARGET_FID column. The result was the creation of a combined dataset that contained both geometric and phenophase attributes. speciesColorMap function was used to identify unique species name from the dataset and assign color to them. styleFeature() and fillcolor was used to draw polygons and apply the assigned color of that species. Legend was created using the buildLegend() functionwhich read the species name from the color map. renderInfo() was used to ensure that the righ-side information keeps on updating when a user clicks on a tree. When the user clicks on the year of the changes the species filter the map redraws with those specific data. This process was computed using the refreshMap() function. Improvements from the previous Beta version include adding a navigation tools such as Zoom to All Features and Reset View button. This was done using button event listener and a helper function called zoomToVisibleFeatures(). This function adjusts the map extent to the current visible tree. Another user interaction feature added to the map was the mouseover and mouseout events so that the tree polygon highlight when the user moves the cursor over them. A highlightSelected() function was introduce to visually emphasize the currently selected tree polygon. Improvements in the left panel was done through using refreshMetric() function. The panel shows the total number of trees, number of visible trees after filtering, number of species, and the selected year. This funtion reads information from the joined dataset and updates HTML elements. The summary panel automatically refresehs whenever the map is updated through the refreshMap() function. The right-side information panel was improved through the renderInfo() function. In the final version, this function presents tree information in a more structured way by grouping values into styled metric boxes rather than showing them as plain text. The new layout uses classes such as .metric, .metric-label, and .metric-value, which made the phenophase values easier to read and compare.