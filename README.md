# CoinRoutes

Order book aggregator in python 
Before beginning, read about how an order book works here 
https://falconair.github.io/2015/01/05/financial-exchange.html​  (  you can ignore the scala bits ) 
 
Since they use slightly non-standard terminology, here are some definitions of terms this description 
uses: 
 
● Bids:​ the line of buyers as referenced in the article.   
○ Array of records.  Each record contains Quantity and price. Sorted by highest price first.  
● Offers:​ The line of sellers as referenced in the article. 
○ Array of records.  Each record contains Quantity and price. Sorted by lowest price first. 
● Order Book​: This is an object that contains the bids and offers data arrays. 
Expected output: 
Write a python program that runs from the terminal, that fetches the order books from  CoinBase Pro 
and Gemini exchanges and prints out the price to buy 10 bitcoin and the price to sell 10 bitcoin.  
 
In the context of the article above, we want to “take” liquidity which means picking people out of their 
place in line: bids side if selling or the offers side if buying.  Bonus: add console log parameters to 
adjust the quantity and add the Kraken exchange 
Resources: 
The exchanges all have JSON REST APIs for fetching order books. 
 
1. CoinBase Pro:  
a. Docs: ​https://docs.pro.coinbase.com/#get-product-order-book 
b. Endpoint for BTC-USD: ​https://api.pro.coinbase.com/products/BTC-USD/book?level=2 
2. Gemini Exchange: 
a. Docs: ​https://docs.gemini.com/rest-api/#current-order-book 
b. Endpoint for BTC-USD: ​https://api.gemini.com/v1/book/BTCUSD 
3. Kraken Exchange(Bonus): 
a. Docs: ​https://www.kraken.com/en-us/features/api#get-order-book 
b. Endpoint for BTC-USD ​https://api.kraken.com/0/public/Depth?pair=XBTUSD 
 
Fetch the order books using requests(or preferred library) . ​https://requests.readthedocs.io/en/master/ 
 
Tips: 
● You will want to normalize the order books into a common format.  You can use standard 
Python Lists for the bids and offers arrays and python dictionaries for the price level objects 
within each bid / offer list 
● You may want to merge the 2-3 order books from each exchange into a single data structure in 
order to generate the output.   
● Order books can be merged across exchanges as long as the resulting merged bids and asks 
data structures are sorted correctly.   
● Bids are typically sorted highest first IE the highest price a seller can sell at, and offers lowest 
first IE the lowest price a buyer can buy at.
