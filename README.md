# python-api-challenge

## Part 1: WeatherPy

<br>In this portion of the challenge, I created a Python script to analyze the relationships between latitude and various weather characteristics for a population of randomly selected cities. To complete this part of the challenge, the following steps were performed:<br><br>

1.	I added my API keys for OpenWeatherMap and Geoapify to the provided api_keys.py file.
The api_keys.py file is maintained on my PC and was added to the .gitignore file for this repository to ensure privacy over my personal API keys<br><br>

2.	I imported the following dependencies:

    * matplotlib.pyplot
    * pandas
    * numpy
    * json
    * requests
    * scipy.stats linregress
    * citipy
    * my OpenWeatherMap API key
    * datetime

    <br>(Note: The starter code imported the time module to convert Unix to a human-readable timestamp. However, I chose to import the datetime module instead. I utilized the information at the following link to learn about the syntax for the datetime module: https://note.nkmk.me/en/python-unix-time-datetime/)<br><br>

3. Using the provided starter code, I generated a list of random cities from the citipy Library, based on a specified range of latitudes and longitudes. The resulting population included 653 cities.<br>

    * Here I added a line of code to the provided starter code to change the city names to title case (cell 2, line 25). This was not a required step – just my personal preference for the aesthetics of the dataframe and the maps that were generated in the second part of the challenge. I tested this first to be sure that changing the case on city name would not impact the OpenWeatherMap API call that followed.<br><br>

4.	Using the provided starter code, I added additional code to set up the OpenWeatherMap API call and retrieve the required weather data. The starter code was set up to skip any cities with missing information. The following information was obtained for each city in the sample population:

    * Latitude
    * Longitude
    * Max Temperature
    * Cloudiness
    * Wind Speed
    * Country
    * Date
    
    <br>As noted above, I used the datetime module to convert the dates from UNIX to a more readable date format, following the example found here:  https://note.nkmk.me/en/python-unix-time-datetime/. This was done based on personal preference and I made sure to confirm that changing the format for the dates would have no unintended downstream consequences.<br><br>

5.	The data obtained in Step 4 above was used to create a dataframe. To check that the data was imported correctly, and assess how many cities were removed as a result of missing information, I printed a record count and sample of the dataframe. The final population included 591 cities.<br><br>

6.	I used the provided code to export the dataframe to a CSV file inside the provided “output_data” folder, creating a new index labeled “City_ID,” then imported the new dataframe from the CSV file to test that the data was transferred successfully.<br><br>

7.	Using the provided images as an example, I generated four scatter plots to visualize the following relationships:

    * Latitude vs. Temperature
    * Latitude vs. Humidity
    * Latitude vs. Cloudiness
    * Latitude vs. Wind Speed

    <br>The figures were printed to the Jupyter notebook and saved to the “output_data” folder as PNG files.<br><br>

8.	Using the .loc function, I created two new dataframes to separate the data by Northern and Southern hemisphere.<br><br>

9.	From the scatter plots generated above, I created a series of new charts for each hemisphere, showing the linear regression for the following relationships:

    * Latitude vs. Temperature
    * Latitude vs. Humidity
    * Latitude vs. Cloudiness
    * Latitude vs. Wind Speed<br><br>

10.	Under each pair of linear regression plots, I added a brief analysis to describe the relationship shown in the visualizations.<br><br>

## Part 2: VacationPy

<br>For the second part of this challenge, I created a Python script to filter the population of cities from Part 1, based on my preferred weather conditions, and identify the nearest hotel for each location. The resulting cities were then plotted on a map to provide a visualization of potential vacation destinations. To complete this part of the challenge, the following steps were performed:<br><br>

1.	I imported the following dependencies:

    * hvplot.pandas
    * pandas
    * requests
    * my Geoapify API key<br><br>

2.	Using the provided code, I imported the city data from the CSV file that was created in Part 1 of the challenge and printed a sample of the dataframe.<br><br>

3.	Following the provided example, I used the hvplot module to generate a map to display the location of each city in the sample population. Per the instructions, I set the size of each point based on the relative humidity.<br>

    * I noticed that the hvplot maps do not display an image in git hub like the matplotlib plots. To make sure there was evidence of my map in the repository, I manually saved a copy of the map image to the output_data folder.<br><br>

4.	Then, I filtered the cities to select for my desired weather conditions. Here, I chose to redefine the name of the dataframe as well, to preserve the original.<br><br>

5.	Per the instructions, I also used the dropna function to remove any rows with missing data.<br>

    * Note:  I debated skipping this step, since the code used in the initial API call would have effectively skipped any cities with missing data, but I did it anyway since it was required. As expected, no additional rows were dropped, as there were no null values.<br><br>

6.	Using the provided starter code, I added code to set up the Geoapify API call and retrieve the closest hotel within a 10,000 meter radius for each city and add the hotel data to a new column in the dataframe. If the call did not return a hotel name, “No hotel found” was added to the “Hotel Name” column instead.<br><br>

7.	A new map was created, using the filtered population of 30 cities. Per the instructions, I added the “Hotel Name” and “Country” fields to the hover text.<br>
    
    * I saved a copy of the map image to the output_data folder just as I did in Step 3 above.
