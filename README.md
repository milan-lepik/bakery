# Bakery - ( Data Flow Boxes )
Divide and conquer!

### Main features:
- split data processing into small reusable boxes
- create flexible pipeline using waterfall and parallel processing
- test your pipeline using API

#### Generators & Boxes
**Generator** generates data into pipeline.
**Boxes** are processing data as one item or batch of items. Box can call external APIs, modify data, save data using databases or APIs.


### Try it!
[Call API api.bakeryjs.com/try-it](https://api.bakeryjs.com/try-it/)

Input example
```
jobInfo: // object with variable input data
    currency: 'bitcoin'
    tweetSearch: 'bitcoin or crypto'
settings: // object with settings for different boxes
    igPosts:
        tick:
            repeatCount: 10
            interval: 1000
    downloadBitfinex: 
        token: 'adjabfk-adjhafjh-adjhfjh-lmfsah'
concurency: 100   // number of pipeline processed in parallel
generate: 'tick'  // name of used generator
process: [  // box pipeline, boxes on one line are processed in parallel, lines are processed as waterfall

    [ 'downloadBitfinex', 'grabTweetSearch', 'grabWeatherForecast' ]
    [ 'analyzeBitcoinVsWeather', 'analyzeBitcoinVsTweets' ]
    [ 'decideOrder', 'saveToMongoDB' ]
    [ 'placeOrderToBitfinex' ]
]
```

### Read more...
Detailed description of each existing Generator or Box [is there.](https://bakeryjs.com/boxes/)
