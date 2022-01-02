# Vacation recommendations based on weather preferences

## Project description

Weather-driven vacation recommendation engine using Google Maps API and Weather API.  Very much a work in progress.

## resources 
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
    * Call API with four cities to generate itinerary.


## Modifications added

* Weather API call:
    * Robust logging for weather API pull
    * Appropriate capitalization for city and country codes pulled from citipy
    * Modified algo to allow for same-named cities in different countries   
* Added data set to map two-digit ISO country code to full country name
* Exploratory analysis of full data set
* Country/City picker: 
    * Print eligible countries for vacations and 
    * Sanitized inputs for min/max temperature


## To-do

### Before initial release

* Self-guided selection of vacation area
    * Allow multiple parameters to narrow data set down to a reasonable amount.  Probably just ask about rain to start.  Requires subjective binning.
        * Keep running tally of values available for trip planning
    * Prompt user to pick eligible country
    * Auto-map itinerary.  Should be ok using `optimize_waypoints` in map call.
        * Would need to do geographic lookups.
    * User will pick starting city once country is chosen and map is selected.
* Add robust logging to google API hotel search?
* Add humidity/wind/etc to selection engine?  If that route is taken, encapsulate into function
    * minima/maxima should be determined by actual values in data set
* Find out why current query from API is pulling data bout the city itself vs the way it was on the assignment
* Bin precipitation by subjective analysis and add to selection engine.

### After initial release

* Save off the JSON files.  Especially google maps, but weather too.
    * THis may be deprioritized for the foreseeable future due to data volume issues and other difficulties storing and identifying data.
* Explore JSON further for potential applications in mapping
* Sort hotels by reviews; add price range.
* Sub-national areas?

## Challenges encountered

* https://www.datahub.io/core/country-list.  Add this to sources list
* Repeating placenames due to countries
* gmaps build
* google scraping considerations - getting nastygrams from google about being a suspected scraper
* JSON