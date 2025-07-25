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
#### Extracted property type from title using keywords like “apartment,” “villa,” “building,” etc.
#### Normalized location names to unify spelling and naming inconsistencies.
#### Added flags for:
#### is_duplicate — if duplicate title/location/price exists.
#### is_luxury — if title contains keywords like “luxury,” “prime,” or “exclusive.”


## Feature Engineering
#### To improve model performance and create meaningful insights from the real estate dataset, the following feature engineering strategies were applied:
#### Created New Features:
#### total_rooms: Sum of bedrooms and bathrooms, representing the overall room count.
#### price_per_bedroom: Price divided by the number of bedrooms — a normalized measure of cost per room.
#### Categorical Encoding:
#### Transformed the following categorical variables into numeric form using Label Encoding:
#### property_type → property_type_encoded
#### title → title_encoded
#### source → source_encoded
#### Feature Scaling:
#### Applied MinMaxScaler to normalize numerical features to a [0, 1] range, ensuring consistent scale across features for models sensitive to scale (e.g., Linear Regression).
#### Saved the scaler as scaler.pkl for reuse in deployment or prediction pipelines.
#### Dropped Irrelevant/Redundant Columns:
#### Removed columns like title and property_type after encoding and size if present, to prevent redundancy or leakage.

## Modeling Approach
#### Two regression models were developed to predict property prices:
#### Linear Regression:
#### A simple, interpretable baseline model.
#### Achieved an R² score of 0.65 and RMSE of ~89,745, indicating moderate performance.
#### Random Forest Regressor:
#### An ensemble model capable of handling non-linear relationships and interactions.
#### Significantly outperformed the linear model with:
#### R² Score: 0.88
#### RMSE: ~52,045
#### Chosen as the final model for deployment.
#### Saved as random_forest_model.pkl.
#### The data was split into training (80%) and testing (20%) sets using train_test_split to evaluate performance fairly and avoid overfitting.


