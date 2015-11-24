# CCM-CS109-Final-Project
Made by Michael Albergo, Curren Iyer, Charles Zhang

These are the APIs we will be using from Ebay:

Shopping API - This will give us access to user data and public item

We want a dataframe of 10,000 users, and the auctions that they have made. All these auctions will have already ended. We will only look at electronics, and perhaps just certain electronics, to not worry about varying price ranges. We will write a weighting function that takes into account increase from starting bid on sell and comparison to average final price for that item. 


What columns we want:
auction_id
user_id
How many items they've sold
Feedback rating
	 - each subcolumn: Iteam as described, Communication, Shipping time, shipping and handling charges
what portion of their feedback is as buyer and as seller
shipping prices
Item Condition
What type of item they are selling?
     - Column for each of the "Item Specifics" infos
Miniumum bid increment
Date of last bid (to see if it changes by season
Count on Item Details
Distance betwen shipper and buyer
Offers returns?
Buy it now? and Buy it now price
Number of Bids and Auction Length


