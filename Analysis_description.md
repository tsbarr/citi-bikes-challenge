# Citibikes Data Challenge

For this challenge, I downloaded the data from the [NYC citibikes system data website](https://citibikenyc.com/system-data).

## Data cleaning and aggregation

The files contain a row for each trip taken in a month. The data changed structure in February 2021, and they stopped reporting trip duration, but I could calculate it by substracting the stop and start times of each trip. I then binned trip duration to facilitate aggregation.

I then performed data cleaning to homogenize the data, giving it the same column names, and dropping rows with missing data, as well as those with trip duration of 0 or less, since that indicates data errors.

After extensive data exploration, I decided to aggregate number of trips in two separate datasets.

For one dataset, I counted the daily number of trips with a certain trip duration bin, user type and rideable type. This is detailed in the following notebook: [Notebooks/citibikes-data-processing1-trip_duration_counts.ipynb](Notebooks/citibikes-data-processing1-trip_duration_counts.ipynb).

The other dataset, I counted the number of monthly trips that used each station, separating them by wether the station was the start or end of the trip. The change in data structure that happened in Feb 2021 also changed the station IDs, so I used station names instead. Also, the coordinates varied in precision for the same station within a month, so I calculated the average coordinates for each station before getting the monthly counts. This process is detailed here: [Notebooks/citibikes-data-processing2-station_counts.ipynb](Notebooks/citibikes-data-processing2-station_counts.ipynb).

This last dataset, which contains station-level data still contained some station names which were different event though they referred to the same station. This was a combination of the station ID changing, which preventing me from using it as a unique identifier, as well as inconsistencies in the data (e.g. North was sometimes just N, or the streets in an interesections would be switched in different records). I attempted to further clean this data, as seen in the last section of the station-counts notebook, but at the end the most effective way was to visually assess the stations in the Tableau map and use the grouping feature to visualize stations that were evidently the same data point together. Doing this, the number of unique stations was reduced by over 200.

## Tableau data story

I used the resulting data sets to generate 9 tableau visualizations (including a dynamic stations map), which I organized in 4 dashboards and 1 data story, which can be accessed here: [NYC Citibike Trip Data Story](https://public.tableau.com/app/profile/tsbarr/viz/citibiketrips_17057061954680/NYCCitibikeTripData).

The key findings are included in a text tile within their corresponding dashboard in the data story.
