## Practice querying from Bay Area Bike Share DB

#### SELECT, FROM, WHERE
1.) The ID's and durations for all trips of duration greater than 500, ordered by duration.
    
    SELECT 
	    bike_id,
	    duration
    FROM trips
    WHERE
	    duration > 500
    ORDER BY duration; 
    
2.) Every column of the stations table for station id 84.

    SELECT *
    FROM stations
    WHERE
	    station_id = 84;
      
3.) The min temperatures of all the occurrences of rain in zip 94301.

    SELECT MinTemperatureF
    FROM weather
    WHERE ZIP=94301 AND PrecipitationIn NOT LIKE (0);

#### Aggregates and Groups
4.) What was the hottest day in our data set? Where was that?

	SELECT MAX(MaxTemperatureF), ZIP
	FROM weather;
	
	Hottest Temperature is 134F and it occurred at ZIP 94063

5.) How many trips started at each station?

	SELECT COUNT(trip_id), start_station
	FROM trips
	GROUP BY start_station;
	
6.) What's the shortest trip that happened?

	SELECT MIN(duration)
	FROM trips;

7.) What is the average trip duration, by end station?

	SELECT AVG(duration), end_station
	FROM trips
	GROUP BY end_station;
	
#### Joins and CTEs

8.) 
