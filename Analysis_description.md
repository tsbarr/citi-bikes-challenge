# Citibikes Data Challenge

For this challenge, I downloaded the data from the [NYC citibikes system data website](https://citibikenyc.com/system-data).

The files contain a row for each trip taken in a month. The data changed structure in February 2021, and they stopped reporting trip duration, but I could calculate it by substracting the stop and start times of each trip. I then binned trip duration to facilitate aggregation.

I then performed data cleaning to homogenize the data, giving it the same column names, and dropping rows with missing data, as well as those with trip duration of 0 or less, since that indicates data errors.

After extensive data exploration, I decided to aggregate number of trips in two separate datasets.

For one dataset, I counted the daily number of trips with a certain trip duration bin, user type and rideable type. This is detailed in the following notebook: [Notebooks/citibikes-data-processing1-trip_duration_counts.ipynb](Notebooks/citibikes-data-processing1-trip_duration_counts.ipynb).

The other dataset, I counted the number of monthly trips that used each station, separating them by wether the station was the start or end of the trip. The change in data structure that happened in Feb 2021 also changed the station IDs, so I used station names instead. Also, the coordinates varied in precision for the same station within a month, so I calculated the average coordinates for each station before getting the monthly counts. This process is detailed here: [Notebooks/citibikes-data-processing2-station_counts.ipynb](Notebooks/citibikes-data-processing2-station_counts.ipynb)
