# Movie Reviews

## Overview

This project fetches movie reviews from The New York Times API and movie details from The Movie Database (TMDb) API, merges the data, cleans it, and exports it to a CSV file for further use.

## Files

- `retrieve_movie_data.ipynb`: Jupyter notebook containing the full implementation of the project.
- `merged_cleaned_data.csv`: The final cleaned and merged dataset exported to a CSV file.

## Prerequisites

- Python 3.x
- Jupyter Notebook
- Libraries: `requests`, `pandas`, `time`, `json`

## Setup

1. **Clone the Repository**:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
Install Dependencies:

bash
Copy code
pip install requests pandas
API Keys:

New York Times API Key: Obtain your API key from New York Times Developer.
TMDb API Key: Obtain your API key from The Movie Database (TMDb).
Usage
Set API Keys:
Update the API keys in the script:

## Implementation Steps

### Part 1: Fetch Data from New York Times API

#### Set the base URL and parameters for the New York Times API request.

#### Create an empty list to store the reviews.

#### Loop through pages 0-19 to fetch movie reviews with "love" in the headline.

- Build the query URL.
- Make a GET request to fetch the data.
- Add a twelve second interval between queries to stay within API query limits.
- Append the fetched reviews to the list.

#### Convert the list of reviews into a pandas DataFrame using `json_normalize()`.

#### Extract movie titles from the `headline.main` column and remove titles containing a period (`.`).

### Part 2: Fetch Data from TMDb API

#### Set the TMDb API key and base URLs.

#### Create an empty list to store the TMDb results.

#### Loop through the titles extracted from NYT reviews.

- Build the search query URL.
- Make a GET request to search for movies by title.
- Extract the movie ID from the search results.
- Build the movie details query URL.
- Make a GET request to fetch the movie details.
- Extract relevant details (genres, spoken languages, production countries, etc.) and store them in a list of dictionaries.
- Add a sleep interval after every 50 requests to stay within API rate limits.

#### Convert the list of movie details into a pandas DataFrame.

### Part 3: Merge, Clean, and Export Data

- Merge the New York Times reviews DataFrame with the TMDb DataFrame on the title column.

- Drop columns containing the word "byline" and "headline.sub".

-  Convert list-like columns to strings and remove unwanted characters (e.g., `[`, `]`, `'`).

- Remove duplicate rows and reset the DataFrame index.

- Export the cleaned DataFrame to a CSV file without the DataFrame's index.

## Contributing
#### feel free to open issues or submit pull requests for improvements and bug fixes.

## Acknowledgements

- [New York Times API](https://developer.nytimes.com/)
- [The Movie Database (TMDb) API](https://www.themoviedb.org/documentation/api)



