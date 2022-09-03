# World_Weather_Analysis

## Retrieve Weather Data

Deliverable 1 requires the retrival of the following information from the API call

Latitude and longitude
Maximum temperature
Percent humidity
Percent cloudiness
Wind speed
Weather description (for example, clouds, fog, light rain, clear sky)
Add the weather data to a new DataFrame 

```Python 
def latitudes(size):
    latitudes = []
    x = 0
    while x < (size):
        random_lat = random.randint(-500, 500) + random.random()
        latitudes.append(random_lat)
        x += 1
    return latitudes
# Call the function with 1500.
%timeit latitudes(2000)
```
Export the DataFrame as WeatherPy_Database.csv into the Weather_Database folder 















