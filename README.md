# Tourist Recommendation Engine - Data Preprocessing and Enrichment

This repository contains the code and resources for the preprocessing and data enrichment of two key datasets: the Places Dataset and the Visitors Preference Dataset, used to build a recommendation engine for tourists visiting Sri Lanka. The objective is to recommend the top 5 places to tourists based on their preferences, ensuring relevance and satisfaction.

## Table of Contents
- [Datasets](#datasets)
- [Preprocessing](#preprocessing)
  - [Places Dataset](#places-dataset)
  - [Visitors Preference Dataset](#visitors-preference-dataset)
- [Data Enrichment](#data-enrichment)
  - [Google Places API](#google-places-api)
  - [External Dataset](#external-dataset)
- [License](#license)

## Datasets

### 1. Places Dataset
This dataset contains information about various tourist destinations in Sri Lanka. It includes columns like:
- Place Name
- Latitude & Longitude
- Address
- Rating
- User ratings total
- User Reviews

### 2. Visitors Preference Dataset
This dataset includes data on tourist preferences. The columns include:
- Tourist Name
- Email
- Preferred Activities
- Bucket List Destinations

## Preprocessing

### Places Dataset
The following steps were performed to clean and prepare the Places Dataset:

1. **Null Value Handling**: Checked for null values in each column.
2. **Duplicate Handling**: 
   - Identified duplicates based on the place name.
   - Merged duplicate rows by combining the latest reviews, averaging latitude, longitude, and ratings, and summing total user ratings.
   - Updated addresses based on correctness and dropped the duplicate row.
3. **Special Characters Removal**: Removed special characters from the names, addresses, and latest reviews.
4. **Address Formatting**: Removed "Sri Lanka" from the address column since all places are in Sri Lanka.

### Visitors Preference Dataset
The preprocessing of the Visitors Preference Dataset included:

1. **Null Value Handling**: Checked for null values in each column.
2. **Name Validation**: Flagged and cleaned entries where the name had fewer than three characters, assuming these were not real names.
3. **Special Characters Removal**: Cleaned special characters from the names, preferred activities, and bucket list destinations.
4. **Duplicate Handling**: 
   - Identified duplicates based on the name column.
   - Merged duplicate rows by combining preferred activities and bucket list destinations.
5. **Email Validation**: Checked for incorrectly formatted email addresses and cleaned them.

## Data Enrichment

### Google Places API
To enrich the Places Dataset and fill in missing ratings and user ratings totals, the Google Places API was used:
- Retrieved `place_ids` of relevant places with missing data.
- Fetched updated ratings and user ratings totals.
- This approach was only partially successful, as data for only 10 places was retrieved.

### External Dataset
To further enrich the dataset, the following external data source was used:
- **Sewwandi, Taniya (2023), “Tourism and Travel Reviews: Sri Lankan Destinations,” Mendeley Data, V1, doi: 10.17632/2nbvx5m4hs.1. Licensed under CC BY 4.0.**
  
Steps taken to integrate this dataset:
1. **Cleaning**: Checked for null values and removed special characters.
2. **Unneeded Columns**: Dropped unnecessary columns for this analysis.
3. **Duplicate Handling**: Merged rows with the same place names by summing user contributions, averaging ratings, and combining text fields.
4. **Data Addition**: Enriched the original Places Dataset with ratings and reviews from this external dataset, although this was successful for only a few places.

## License
This project uses data from an external dataset licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Modifications were made to the dataset to enrich the analysis.
