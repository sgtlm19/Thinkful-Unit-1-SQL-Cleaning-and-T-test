## AirBnB Cities Challenge ##

1.) What's the most expensive listing(s)? What else can you tell me about the listing(s)?

    -- Find most expensive listing
    SELECT MAX(price)
    FROM la_listings;
    
    -- Most expensive listing is $10,000.00, lets see what the listing looks like
    SELECT *
    FROM la_listings
    WHERE price = '10000';




2.) What neighborhoods seem to be the most popular?
