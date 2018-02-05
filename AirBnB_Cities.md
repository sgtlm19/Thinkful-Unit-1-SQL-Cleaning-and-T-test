## AirBnB Cities Challenge ##

1.) What's the most expensive listing? What else can you tell me about the listing?

    -- Remove $ sign from Price variable
    UPDATE listings
    SET price = REPLACE(price, '$', '');
    
    -- Find most expensive listing
    SELECT MAX(price)
    FROM listings;
    
    -- Most expensive listing is $9,999.00, lets see what the listing looks like
    SELECT *
    FROM listings
    WHERE price = '9,999.00';
