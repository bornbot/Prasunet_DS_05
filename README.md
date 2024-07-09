# Geo Data Project

- [Introduction](#introduction)
- [Overview](#overview)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [File Decription](#file-descriptions)
- [Usage](#usage)
- [Contribution](#contributing)
- [License](#license)
- [Acknowledgement](#acknowledgements)

## Introduction
This project focuses on analyzing UK traffic accident data to uncover patterns related to road conditions, weather, and time of day. By visualizing accident hotspots and contributing factors, the analysis aims to provide insights that can help improve road safety and reduce the frequency of accidents. The project leverages Python, pandas, and seaborn for data processing and visualization, offering a comprehensive view of the factors influencing traffic accidents.

## Overview
This project visualizes geographical data related to UK accidents using HTML, JavaScript, and the Leaflet.js library. The goal is to create an interactive heat map displaying accident data points across a specific region, providing insights into the distribution and frequency of accidents.

## Project Structure
- `Geo_data.html`: Contains the HTML and JavaScript code to render the geographical data on a map using the Leaflet.js library.
- `UK_Accident.csv`: A CSV file that includes detailed data about accidents in the UK. This data is used to generate the heat map visualization.
- `DS_05.ipynb`: A Jupyter notebook that contains data processing and analysis code used to prepare the data for visualization.

## Getting Started
### Prerequisites
- Web browser (e.g., Chrome, Firefox)
- Basic understanding of HTML, CSS, and JavaScript

### Setup
1. **Clone the Repository:**
   ```bash
   git clone <repository-url>
   cd <repository-directory>

2. Open the HTML File:
   Open the Geo_data.html file in your web browser to view the map visualization.

## File Descriptions
### Geo_data.html
This HTML file uses the Leaflet.js library to create an interactive map and visualize accident data as a heat map.

#### Code Explanation:
- Meta Tags and Scripts:
Includes various meta tags and script links for Leaflet.js, jQuery, Bootstrap, and Awesome Markers.
- Styles:
Styles for HTML and body to ensure full width and height, and specific styling for the map container.
- Leaflet.js Initialization:

``` html
<script>
    var map = L.map('map').setView([51.5074, -0.1278], 12);
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
        attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
    }).addTo(map);

    var heat = L.heatLayer([
        [51.505, -0.09, 0.2], // Example coordinates with intensity
        [51.51, -0.1, 0.5],
        [51.51, -0.12, 0.8]
    ], {radius: 25}).addTo(map);
</script>
```
 
- Initializes the map centered on London with a zoom level of 12.
- Adds OpenStreetMap tile layer to the map.
- Adds a heat map layer with example data points.

### UK_Accident.csv
This CSV file contains accident data with information such as location (latitude and longitude), date, and severity of accidents. This data is visualized on the map as a heat map.

### DS_05.ipynb
This Jupyter notebook contains the data processing steps necessary to prepare the accident data for visualization.

#### Code Explanation:
1. Import Libraries:

```python
import pandas as pd
import folium
from folium.plugins import HeatMap
```
2. Load Data:

``` python
data = pd.read_csv('UK_Accident.csv')
```
3. Data Preprocessing:

Clean and filter the data to ensure it's ready for visualization.
```python
data = data[['Latitude', 'Longitude', 'Accident_Severity']]
data = data.dropna()
```
4. Create Heat Map:

- Create a base map centered on a specific location.
```python
map_ = folium.Map(location=[51.5074, -0.1278], zoom_start=12)
```
- Convert the DataFrame to a list of lists and create a HeatMap layer.
```python
heat_data = [[row['Latitude'], row['Longitude']] for index, row in data.iterrows()]
HeatMap(heat_data).add_to(map_)
```
5. Save the Map:

- Save the heat map as an HTML file.
```python
map_.save('Geo_data.html')
```
## Usage
- Open the Geo_data.html file in a web browser to see the geographical data visualization.
- Use the Jupyter notebook to preprocess any new data before adding it to the visualization.

## Contributing
If you wish to contribute to this project, please follow these steps:

Fork the repository.
1. Create a new branch (git checkout -b feature-branch).
2. Commit your changes (git commit -m 'Add new feature').
3. Push to the branch (git push origin feature-branch).
4. Create a new Pull Request.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgements
- [Leaflet.js](https://leafletjs.com/)
- [Folium](https://python-visualization.github.io/folium/)
- [Bootstrap](https://getbootstrap.com/)
## Contact
For any questions or feedback, please contact Sanskriti Ojha at [ojhasanskriti08.09@gmail.com].

