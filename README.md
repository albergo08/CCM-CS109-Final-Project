# CCM-CS109-Final-Project
Made by Michael Albergo, Curren Iyer, Charles Zhang

These are the APIs we will be using from Ebay:

Shopping API - This will give us access to user data and public item

Finding API - This will give us access to auction data

We want a dataframe of 10,000 users, and the auctions that they have made. All these auctions will have already ended. We will only look at electronics, and perhaps just certain electronics, to not worry about varying price ranges. We filter by items sold in US only. We will write a weighting function that takes into account increase from starting bid on sell and comparison to average final price for that item. 


**What columns we want:**

item_id: 

    - the id associated with the item being auctioned/sold. 
    - example: "121829321531"

user_id:

    - the user who listed the item. e
    - example: "basbalmom27"

	 - each subcolumn: Item as described, Communication, Shipping time, shipping and handling charges
what portion of their feedback is as buyer and as seller
=======
n_sold: 

    - How many items they've sold in the past. Comes from FeedbackScore item in GetUserProfile.
    - example: "FeedbackScore: 140"
        

Feedback rating and each subcolumn

    - these come from AverageRatingDetails in GetUserProfile in Shopping API
        - Item as described    
        - Communication
        - Shipping time
        - Shipping and handling charges


cost_ship:
    
    - the cost charged to the buyer for shipping, retrieved from Finding API
    - example: __value__: "0.0"

n_ship_locs:
    
    - the number of countries the seller is willing to ship to. Sum of shipToLocations item in Finding API
    - example: count up "AU", "JP", "Americas", "Europe"

expeditable:
    
    - Boolean stating if expedited shipping is available or not, found in expeditedShipping in Finding API

oneDay:
    
    - Boolean stating if one-day shipping is available or not, found in oneDayShippingAvailable in Finding API

last_price: 

    - the final price at the end of the auction/selling period (even if it sold or not). found in sellingStatus in Finding API
    - example: currentPrice __value "299.99"

bid_count:

    - number of bid placed on the item. Found in sellingStatus in Finding API
    - example: "0"

bestOfferEnabled:

    - boolean about whether or not best off was enabled. Found in listingInfo in Finding API

buyItNowAvailable:
    
    - boolean about whether or not buy it now is available. Found in listingInfo in Finding API

listing Type:

    - Either or Auction or list price or best offer. We will convert these to numbered values to do analysis. In same location as above

returnsAccepted:

    - boolean about whether returns are acceped or not. In Finding API

conditionId:

    - value associated with New, Used, Like New, Good etc. example: "1000" is New

topRatedListing:

    - is it a top rating? boolean



Still want Miniumum bid increment

still want Date of last bid (to see if it changes by season

Still wantCount on Item Details

Still wantDistance betwen shipper and buyer

Still wantNumber of Bids and Auction Length


Steps to consolidating information between different APIs:
1. findCompletedItems from Finding API
2. getSingleItem from Shopping API
3. getUserProfile from Shopping API


