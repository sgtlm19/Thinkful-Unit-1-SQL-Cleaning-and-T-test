## AirBnB Cities Challenge ##

1.) What's the most expensive listing(s)? What else can you tell me about the listing(s)?

    -- Find most expensive listing
    SELECT MAX(price)
    FROM la_listings;
    
    -- Most expensive listing is $10,000.00, lets see what the listing looks like
    SELECT *
    FROM la_listings
    WHERE price = '10000';
    
    The most expensive listings are in very rich neighborhoods: Hollywood, Beverly-Hills, and Malibu.




2.) What neighborhoods seem to be the most popular?

    -- Set up the CTE to create a 'count_reviews' table
    WITH 
	    count_reviews
    AS (
        -- Simple query that takes the count of each listing_id
        SELECT 
		    COUNT(listing_id) counts, 
		    listing_id
	    FROM reviews
	    GROUP BY listing_id
	)
	-- Join the 'count_reviews' table with the 'la_listings' table on listing_id
    -- Get count listing_ids, aggregate that count by neighborhood, group by nieghborhood, and order by count
    SELECT 
	    COUNT(c.counts),
	    l.neighborhood
    FROM 
	    count_reviews c
    JOIN 
	    la_listings l
    ON
	    c.listing_Id = l.listing_ids
    GROUP BY neighborhood
    ORDER BY COUNT(c.counts) DESC
    LIMIT 10;
    
 3.) What time of year is the cheapest time to go to your city? What about the busiest?
 
     -- Cheapest time of the year is May, it has cheapest average price during the year
     
     -- I created a months column and set it to the month of the date column
        UPDATE calendar
        SET months = STRFTIME('%m', date);
     
     -- I removed the dollar sign from the prices column
        UPDATE calendar
        SET prices = REPLACE(prices, '$', '');
        
     -- I removed the comma from the prices column
        UPDATE calendar
        SET prices = REPLACE(prices, ',', '');
        
     -- I found the average listing price for each month
        SELECT AVG(prices),
            months
        FROM calendar
        GROUP BY months
        ORDER BY AVG(prices);
        
     
     -- Busiest time of the year is March
     SELECT 
	    COUNT(listing_id),
	    STRFTIME('%m', date) AS month
     FROM reviews
     GROUP BY month
     ORDER BY COUNT(listing_id) DESC;
     
