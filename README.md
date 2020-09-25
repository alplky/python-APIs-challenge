# python-APIs-challenge

## WeatherPy
### Objective:

Create a Python script to visualize the weather of 500+ cities across the world of varying distance from the equator. Then compare max temperatures, wind speed, humidity, and cloudiness to the latitude and discover any trends. 

#### Generating a List of Random Cities

A list of 500 + random cities was created by making two variables with the respective ranges of latitude and longitude, then zipping the lists together into a new list. The cities were found by utilizing citipy in a for loop to append the city names to an empty list. 

#### Perform API Calls

To start off, a function was defined to extract data from the JSON output that included the name, lat, long, max temperature, humidity, cloudiness, windspeed, country, and data. The data was retrieved by using the OpenWeatherMap API in a for loop enumerating over the list of coordinates. A print log was extablished to print out the record number and city as the data was being process. In order to not halt the retrieval, a try/except was implemented within the for loop and would print out if a city was not found. The data was extracted and appended to an empty list, then converted into a data frame and output to a csv. 

#### Plotting Weather Data

Next, plots were created from the data that was retrieved during the API calls to observe any weather trends when compared along the latitude for both the northern and southern hemisphere. Then additional plots were made, separating the latitudes into southern and northern hemispheres to compare the weather trends and linear regression respectively.

![Max_Temp](WeatherPy/Images/max_temp_plot.png)

![Humidity](WeatherPy/Images/humidity_plot.png)

![Cloudiness](WeatherPy/Images/cloudiness_plot.png)

![Wind_Speed](WeatherPy/Images/windspeed_plot.png)

![NH_Temp](WeatherPy/Images/northern_maxtemp_plot.png)

![SH_Temp](WeatherPy/Images/southern_maxtemp_plot.png)

![NH_Humidity](WeatherPy/Images/northern_humidity_plot.png)

![SH_Humidity](WeatherPy/Images/southern_humidity_plot.png)

![NH_Cloudiness](WeatherPy/Images/northern_cloudiness_plot.png)

![SH_Cloudiness](WeatherPy/Images/southern_cloudiness_plot.png)

![NH_Wind_Speed](WeatherPy/Images/northern_windspeed_plot.png)

![SH_Wind_Speed](WeatherPy/Images/southern_windspeed_plot.png)

## VacationPy
### Objective:

Plan future vacations but using the previously made city weather csv to find locations with the most ideal weather. 

#### Create a Data Frame of Cities with Ideal Weather

This dataframe was created by dropping rows with the max temperature over 90 or under 60, windspeeds over 10 mph, and cloudiness abover 40%

#### Obtain First Hotel in each City Using Google Places API

For vacation planning, the first step is always to look at hotels in each city. This was done using Google Places Nearby Search API. The location parameter takes a very specific format of coordinates, so a new column was added to the dataframe by adding the latitude and longitude columns together, as strings, and separated by a comma. Similar to processing the weather APIs, first an extract function was define followed by a for loop iterating over the combined lat/lng column as a list. A record was printed for each coordinates in the try/except block to note when a hotel was found or not. The data was then extracted, appended to an empty list, and turned into a dataframe.

#### Merging Data Frames and Plotting

In order to merge the city weather data frame with the new hotels data frame, first the latitude and longitude columns needed to be rounded to the 0 decimal. Anything larger than 0 would not match up in the merge. The columns were then renamed for cleaner output in map plot. 

The merged data frame was plotted using Plotly and Mapbox with the latitude and longitude of the hotels. The heatmap was created by assigning the Humidity column to color which colors cities by humidity percentage. Hover data shows the coordates, city, country, hotel name, and humidity for each plot point. 

![SH_Wind_Speed](VacationPy/Images/mapbox_heatmap.png)



