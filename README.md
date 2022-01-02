# Vacation recommendations based on weather preferences

## Project description

Weather-driven vacation recommendation engine using Google Maps API and Weather API.  Based on a set of 2,000 randomly generated lat/long coordinates, identify the nearest city to each one, extract current weather details, and then allow a user to plan a vacation in a given country based on weather preferences.

## Tech Resources 
* Anaconda3 (2021.11)
* Jupyter Lab (3.2.1)
* Python (3.7.11)
    * Pandas module (1.3.4)
    * Numpy module (1.20.3)
    * citiPy (0.0.5)
    * matplotlib (3.4.3)
    * requests library (2.26.0)
    * gmaps
* Visual Studio Code (1.63.2)

## Data Sources

* weather api
* google api
* https://www.datahub.io/core/country-list

## Original request

* Script 1 (weather database):
    * Generate 2k random lat/long coordinates
    * Cross-reference with citypy to identify nearest city.
    * Use weather API to identify current weather in all identified cities and save data to csv
* Script 2 (vacation search):
    * run cities from weather data csv through google maps API
        * identify hotels from API and add to JSON file.
* Script 3 (vacation itinerary)
    * Map out potential destinations hotels identified by Script 2.
    * User manually identifies four cities in a single country and hard-codes them into script.
    * Call API with four cities to generate itinerary

## Modifications added

* Weather API call:
    * Robust logging for weather API pull
    * Appropriate capitalization for city and country codes pulled from citipy
    * Modified algo to allow for same-named cities in different countries   
* Added data set to map two-digit ISO country code to full country name
* Exploratory analysis of full data set
* Country/City picker: 
    * Print eligible countries for vacations and prompt user to re-run if none have at least 4 locations.
    * Sanitized inputs for min/max temperature
    * Added robust logging to Google places API hotel search
* Vacation itinerary:
    * Self-guided selection of vacation area using UI inputs rather than hard-coded values:
        * Allow user to pick country for vacation.
        * Allow user to select cities for itinerary.
        * Auto-map itinerary using using `optimize_waypoints=True` in map call.

## Potential future enhancements

* More Self-guided selection of vacation area
    * Allow multiple parameters to narrow data set down to a reasonable amount.  Probably just ask about rain to start.  Requires subjective binning.
        * Keep running tally of values available for trip plannin
    * Auto-map itinerary.
        * Could use criteria to match weather, etc?
    * User will pick starting city once country is chosen and map is selected.
* Add humidity/wind/etc to selection engine?  If that route is taken, encapsulate into function
    * minima/maxima should be determined by actual values in data set
* Bin precipitation by subjective analysis and add to selection engine.
* Save the JSON files to local environment automatically during pull.
    * Explore JSON further for potential ehancements to application.
    * THis may be deprioritized for the foreseeable future due to data volume issues and other difficulties storing and identifying data.
* Sort hotels by reviews; add price range.
* Sub-national areas?

## Challenges encountered

* Info boxes are ugly.
* https://www.datahub.io/core/country-list.  Add this to sources list
* Repeating placenames due to countries
* gmaps build
* google scraping considerations - getting nastygrams from google about being a suspected scraper
* JSON
* type = "logding" --why current query from API is pulling data bout the city itself vs the way it was on the assignment