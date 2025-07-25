# DataSiencenceWebScrape

## Real Estate Data Scraping and Cleaning Project
### Objective
#### The goal of this project is to scrape property listings from popular Omani real estate websites and build a clean, structured dataset for analysis. This dataset can support future efforts like price prediction, location-based analysis, and identifying market trends.

## Websites Used
#### VistaOman.com — scraped 'For Sale' listings only.

#### Tibiaan.com — focused on 'For Sale' listings (not rentals).

## Steps Taken
#### 1. Web Scraping
##### Vista Oman:
#### Used Selenium to simulate clicks on the "For Sale" filter.
#### Clicked "Load More" to load all listings.
#### For each property, visited the detail page to extract:
### Title, Price, Bedrooms, Bathrooms, Location (if available, if not we extracted it from the title during the cleaning process)

#### Tibiaan:
#### Extracted similar fields by identifying structured listing blocks.
#### Noted that type (Apartment, Villa, etc.) was embedded in the title, and was later extracted using keyword matching.

## Data Cleaning
#### Cleaned all price fields by:
#### Removing non-numeric characters anf filling price, bedroom, bathroom nulls with mean as for location we used the mode
#### Normalized title fields by lowercasing and stripping extra spaces for duplicate detection.


## Feature Engineering
#### Extracted property type from title using keywords like “apartment,” “villa,” “building,” etc.
#### Normalized location names to unify spelling and naming inconsistencies.
#### Added flags for:
#### is_duplicate — if duplicate title/location/price exists.
#### is_luxury — if title contains keywords like “luxury,” “prime,” or “exclusive.”

