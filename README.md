# CCM-CS109-Final-Project
Made by Michael Albergo, Curren Iyer, Charles Zhang

These are the APIs we will be using from Ebay:

Shopping API - This will give us access to user data and public item

Finding API - This will give us access to auction data

We want a dataframe of 10,000 users, and the auctions that they have made. All these auctions will have already ended. We will only look at electronics, and perhaps just certain electronics, to not worry about varying price ranges. We filter by items sold in US only. We will write a weighting function that takes into account increase from starting bid on sell and comparison to average final price for that item. 


**What columns we want:**

item_id: 

    - the auction itemID. 
    - example: "121829321531"
    - inside searchResults under item

user_id:

    - the user who listed the item. 
    - example: "basbalmom27"


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




**Things that we can get from getSingleItem Shopping API call:**

Get itemID again:

    - inside Item
    - this is to add on to existing Finding API data

EndTime:

    - returns time the bid ends
    - inside Item

StartTime:

    - returns start time of bid. Can be used with EndTIme to calculate Auction duration
    - inside Item

ListingType:

    - Returns type of listing.
    - example: "FixedPriceItem"
    - inside Item

Location:

    - Returns string location in form City, State (in US)
    - inside Item

PictureURL_count:

    - PictureURL inside Item. we want the len of PictureURL array

PostalCode:

    - returns string of numbers
    - inside Items

UserID:

    - inside Seller which is inside Item
    - example: "my-ohnogto"

BidCount:

    - number of bids placed on item
    - inside Items

FinalPrice:
    
    - the CurrentPrice value for completed auctions
    - we want Value inside Current Price, which is inside Items

ShipToLocations_count:

    - How many states/countries will seller ship to. 
    - take count of ShipToLocations in Items

ReturnPolicy:

    - gives string "ReturnsNotAccepted" or "ReturnsAccepted". Convert to bool
    - inside Items

ProductID:

    - gives ID for type of product being auctioned in terms of some string of numbers. Idk what we will use for yet
    - get Value inside ProductID, which is inside items


handlingTime:

    - gives int 1,2,3,4,etc which indicates how many days of handling the seller will take to ship
    - inside Items

GlobalShipping:

    - bool that says whether they'll ship out of US or not.
    - inside Items





**Shopping API for User data per UserID**

FeedbackScore: 

    - How many items the user has had positive interactions with. Comes from FeedbackScore item in GetUserProfile.
    - example: "FeedbackScore: 140"
    - IF we wanted to improve on our model as a separator for just sellers, we would find a way to get Selling only feedback score. Currently, Feedback score is an aggregate of feedback as a buyer and as a seller. It's an important number even if we don't do that, still.'

SellerBusinessType:

    - returns string like "Undefined" or "Commercial" or "Private"
    - inside User

ItemAsDescribed:

    - returns average rating for how accurate the seller described the item
    - Is Rating for the RatingDetal:"ItemAsDescribed" inside AverageRatingDetails inside FeedbackHistory

Communication:

    - returns average rating for seller's communication
    - Is Rating for the RatingDetal: "Communication" inside AverageRatingDetails inside FeedbackHistory

ShippingTime:

    - returns average rating for how quick the seller shipped
    - Is Rating for the RatingDetal: "ShippingTime" inside AverageRatingDetails inside FeedbackHistory


S&H_Charges:

    - returns average rating for how reasonable seller's' shipping costs were
    - Is Rating for the RatingDetal: "ShippingAndHandlingCharges" inside AverageRatingDetails inside FeedbackHistory







Still want Miniumum bid increment

still want Date of last bid (to see if it changes by season

Still wantCount on Item Details

Still wantDistance betwen shipper and buyer

Still wantNumber of Bids and Auction Length


Steps to consolidating information between different APIs:
1. findCompletedItems from Finding API
2. getSingleItem from Shopping API
3. getUserProfile from Shopping API


