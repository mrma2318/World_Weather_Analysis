# World_Weather_Analysis

## Collect and present data for customers where they will can filter on PlanMyTrip on their preferred travel criteria in order to find their ideal hotel, anywhere in the world.

### The purpose of this analysis, PlanMyTrip wants to take their app to the next level. To assist them, they wanted me to add weather descriptions to the weather data, and create input statements so testers could input their weather preferences and identify potential travel destinations with nearby hotels. In addition, use Google Maps Directions to create a travel route between the potential travel destinations with markers on the map. 

## Analysis
- To assist PlanMyTrip take their app to the next level, I needed to first generate a set of 2,000 random latitudes and longitudes, retrieve the nearest cities, and perform an API call with OpenWeatherMap. To generate a new set of 2,000 random latitudes and longitudes, I used the np.random.uniform function. The random function connected to the NumPy module allows me to generate a floating-point decimal number between two numbers (or a lower boundary and an upper boundary). When generating 2,000 latitudes and longitudes, it's important to remember that 30% of the Earth is made up of bodies of water though. Therefore, I needed to use the citipy module to get the nearest city for each latitude and longitude. 

- Next I can import my OpenWeatherMap's and assemble the API call URL as a string variable. From my API call I retrieved information on the following: latitude and longitude, maximum temperature, percent humidity, percent cloudiness, wind speed, and weather description. Now that I made my API call, I can turn the weather data into a new DataFrame, Table 1. 

### Table 1: Weather Data

![Weather Data](https://github.com/mrma2318/World_Weather_Analysis/blob/6445ec587fcb123915d913fbd033b4adba750829/Resources/WeatherData.png)

- Now that I have the weather data in a DataFrame, I can generate input statements to retrieve customer weather preferences. Then I'll use those preferences to identify potential travel destinations and nearby hotels. The input statements, Image 1, allow the customer to put in their minimum and maximum temperatures they want to stay within for planning their vacation. In Image 1, you can see the minimum temperature preference for that customer is 75 degrees Fahrenheit, and their maximum temperature is 90 degrees Fahrenheit. Now we can use those temperatures to generate preferred cities that meet that criteria. 

### Image 1: Input Statements

![Input Statements](https://github.com/mrma2318/World_Weather_Analysis/blob/74c6d14bf489be9ee3f7833ec83b7d7e7f6cad42/Resources/Input_Statements.png)

- Since we know their temperature preferences, we can show those destinations on a marker layer map with pop-up markers. First, I needed to review the hotel parameters so that I could search for a hotel in each city. Then I created a for loop to go through the DataFrame I was working with to retrieve the latitude and longitude of each city to find the nearest hotel based on the search parameters. If a hotel was found, then I had it added to the DataFrame for that city. If a hotel was not found, then I had the code skip and go to the next one. I also dropped all the rows that a hotel was not found, and stored the cities that did have a hotel into a new DataFrame. This way, when generating the Google Map, the data is clean, the code will run more smoothly, and will provide accurate information on the Google Map.

- Finally, I can put together an information box and generate a Google Map with the destinations in their temperature preferences with a hotel for each city, Image 2. 

### Image 2: Weather Vacation Map

![Weather Vacation Map](https://github.com/mrma2318/World_Weather_Analysis/blob/af7aa1cda16e8966b84076f6845c9ee4335fa9fb/Vacation_Search/WeatherPy_vacation_map.png)

- So our customer has chosen their temperature preferences, has chosen to go to Saudi Arabia for their trip, and has selected four cities they want to travel to while in Saudi Arabia Mecca, Riyadh, Buraydah, and Umm Lajj. Therefore, I used the gmap documentation to create a directions layer map using the cities the customer wants to visit, Image 3. 

### Image 3: Weather Travel Map

![Weather Travel Map](https://github.com/mrma2318/World_Weather_Analysis/blob/af7aa1cda16e8966b84076f6845c9ee4335fa9fb/Resources/Weather%20Vacation%20Map.png)

- Now that we have the customers destinations and their travel map of their four destinations, I can refactor my code and create another map layer that shows the information boxes of the four cities. Therefore, I first needed to use the concat() function to put the four cities into their own DataFrame. This way when I refactor my code, it will focus only on the four cities they want to travel to instead of all the cities around the world that meet their original critieria. 

### Refactored Weather Map Code

![Refactored Weather Map Code](https://github.com/mrma2318/World_Weather_Analysis/blob/967f67c4160b21b9bcca5b9ae7c6e29ba5d900a4/Resources/Refactored%20Weather%20Map%20Code.png)

### Image 4: Weather Map Itinerary

![Weather Map Itinerary](https://github.com/mrma2318/World_Weather_Analysis/blob/967f67c4160b21b9bcca5b9ae7c6e29ba5d900a4/Vacation_Itinerary/WeatherPy_travel_map_markers.png)

## Summary
- I was able to successfully assist PlanMyTrip take their app to the next level by helping customers choose their temperature minimum and maximum requirements, choose travel destinations, and provide a travel destination map and information. The temperature requirements allow customers to choose a temperature range they would like to stay in for their trip. Once the map generates map markers with their desired temperature requirements, they can search the destinations to pick where they want to go. Once they decide where they want to go, the map provides hotels in each city, where the customer can choose destinations to travel to while in that country. Finally, after they decide where they want to travel to, we can show them a map with the travel destinations and the itinerary of each city they want to travel to. 

- There are some limitations to this analysis though. The map only provides one hotel per city, so customers don't have multiple options of hotels to chose from in one city. The hotel that is provided on the map, may not be the hotel customers want to stay at and could potentially search for other hotels on another app. 

- Another limitation to this analysis is that the travel destination does not provide the amount of time it takes to travel to the different cities. It provides a map layout and the path you want to take, but it doesn't provide the time it takes to get from one city to the next. 
