# World_Weather_Analysis

## Retrieve Weather Data

Deliverable 1 requires the retrival of the following information from the API call:
Latitude and longitude,
Maximum temperature,
Percent humidity,
Percent cloudiness,
Wind speed,
Weather description (for example, clouds, fog, light rain, clear sky),
Add the weather data to a new DataFrame. 

``` Python
# Loop through all the cities in the list.
for i, city in enumerate(cities):

    # Group cities in sets of 50 for logging purposes.
    if (i % 50 == 0 and i >= 50):
        set_count += 1
        record_count = 1
        time.sleep(60)

    # Create endpoint URL with each city.
    city_url = url + "&q=" + city.replace(" ","+")

    # Log the URL, record, and set numbers and the city.
    print(f"Processing Record {record_count} of Set {set_count} | {city}")
    # Add 1 to the record count.
    record_count += 1
# Run an API request for each of the cities.
    try:
        # Parse the JSON and retrieve data.
        city_weather = requests.get(city_url).json()
        # Parse out the needed data.
        city_lat = city_weather["coord"]["lat"]
        city_lng = city_weather["coord"]["lon"]
        city_max_temp = city_weather["main"]["temp_max"]
        city_humidity = city_weather["main"]["humidity"]
        city_clouds = city_weather["clouds"]["all"]
        city_wind = city_weather["wind"]["speed"]
        city_country = city_weather["sys"]["country"]
        
        for i in city_weather['weather']:
            city_description=i["description"]        
        # Convert the date to ISO standard.
        city_date = datetime.utcfromtimestamp(city_weather["dt"]).strftime('%Y-%m-%d %H:%M:%S')
        # Append the city information into city_data list.
        city_data.append({"City": city.title(),
                          "Country": city_country,
                          "Lat": city_lat,
                          "Lng": city_lng,
                          "Max Temp": city_max_temp,
                          "Humidity": city_humidity,
                          "Cloudiness": city_clouds,
                          "Wind Speed": city_wind,
                          "Description": city_description})
# If an error is experienced, skip the city.
    except:
        print("City not found. Skipping...")
        pass

# Indicate that Data Loading is complete.
print("-----------------------------")
print("Data Retrieval Complete      ")
print("-----------------------------")
Export the DataFrame as WeatherPy_Database.csv into the Weather_Database folder 
```

![deliverable 1 ](https://user-images.githubusercontent.com/104809098/188253108-91c827c1-3dda-4bb6-a796-9f3514635d38.png)

## Create a Customer Travel Destinations Map

A marker layer map with pop-up markers for the cities in the vacation DataFrame is created, and it is uploaded as a PNG. Each marker has the following information:
Hotel name,
City,
Country,
Current weather description with the maximum temperature.

![deliverable 2](https://user-images.githubusercontent.com/104809098/188253252-aeeefe0f-5d3f-4a38-98e5-a9033c19723e.png)


## Create a Travel Itinerary Map

Used the Google Directions API to create a travel itinerary that shows the route between four cities chosen from the customer’s possible travel destinations. Then, created a marker layer map with a pop-up marker for each city on the itinerary.

![vacation_itenerary_map3](https://user-images.githubusercontent.com/104809098/188253312-deb5a231-d7f7-46bb-8d26-93af4586cba4.png)

![WeatherPy_travel_map_markers](https://user-images.githubusercontent.com/104809098/188253364-8a48813d-7bc5-4925-b6eb-bf9c30edbe71.png)



