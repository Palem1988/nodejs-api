CryptoControl Crypto News API
=========================

Official Node.js client for the [CryptoControl.io](https://cryptocontrol.io) API. The CryptoControl Node.js client lets developers access rich formatted articles from cryptonews sources from all around the world.

## Installation
### Node
```sh
npm install crypto-news-api --save
```

### Bower - Browser/Web
```sh
bower install crypto-news-api --save
```
```html
<script src="./bower_components/crypto-news-api/dist/bundle.js"></script>
```

## Usage
First make sure that you've recieved an API key by visiting [https://cryptocontrol.io/apis](https://cryptocontrol.io/apis). With the API key, you can write the following code.

**NOTE**: API access is rate-limited to 5 req/sec and 10,000 req/hour. It'll be a good idea to cache your API calls.


### Node.js ES6/Typescript
```javascript
import CryptoNewsApi from 'crypto-news-api'

const Api = new CryptoNewsApi('API_KEY_HERE')

Api.getTopNews()
    .then(articles => console.log(articles))
    .catch(error => console.error(error))


Api.getTopNewsByCoin("bitcoin")
    .then(articles => console.log(articles))
    .catch(error => console.error(error))


Api.getLatestTweetsByCoin("bitcoin")
    .then(tweets => console.log(tweets))
    .catch(error => console.error(error))


Api.getLatestRedditPostsByCoin("bitcoin")
    .then(redditPosts => console.log(redditPosts))
    .catch(error => console.error(error))
```

### Node.js ES5
```javascript
var CryptoNewsAPI = require('crypto-news-api').default

const Api = new CryptoNewsAPI('API_KEY_HERE')

Api.getTopNews()
    .then(function (articles) { console.log(articles) })
    .catch(function (error) { console.log(error) })


Api.getTopNewsByCoin("bitcoin")
    .then(function (articles) { console.log(articles) })
    .catch(function (error) { console.log(error) })


Api.getLatestTweetsByCoin("bitcoin")
    .then(function (tweets) { console.log(tweets) })
    .catch(function (error) { console.log(error) })


Api.getLatestRedditPostsByCoin("bitcoin")
    .then(function (redditPosts) { console.log(redditPosts) })
    .catch(function (error) { console.log(error) })
```

### Bower/Webpack
```html
<script src="./bower_components/crypto-news-api/dist/bundle.js"></script>
<script>
    const Api = new window.CryptoNewsApi('API_KEY_HERE')

    Api.getTopNews()
        .then(function (articles) { console.log(articles) })
        .catch(function (error) { console.log(error) })


    Api.getTopNewsByCoin("bitcoin")
        .then(function (articles) { console.log(articles) })
        .catch(function (error) { console.log(error) })


    Api.getLatestTweetsByCoin("bitcoin")
        .then(function (tweets) { console.log(tweets) })
        .catch(function (error) { console.log(error) })


    Api.getLatestRedditPostsByCoin("bitcoin")
        .then(function (redditPosts) { console.log(redditPosts) })
        .catch(function (error) { console.log(error) })
</script>
```

## Available Functions

- **getTopNews()** Get the top news articles.
- **getLatestNews()** Get the latest news articles.
- **getTopNewsByCategory()** Get news articles grouped by category.
- **getTopNewsByCoin(coinSlug: String)** Get the top news articles for a specific coin.
- **getLatestNewsByCoin(coinSlug: String)** Get the latest news articles for a specific coin.
- **getTopNewsByCoinCategory(coinSlug: String)** Get news articles grouped by category for a specific coin.
- **getTopRedditPostsByCoin(coin: String)** Get top reddit posts for a particular coin
- **getLatestRedditPostsByCoin(coin: String)** Get latest reddit posts for a particular coin
- **getTopTweetsByCoin(coin: String)** Get top tweets for a particular coin
- **getLatestTweetsByCoin(coin: String)** Get latest tweets for a particular coin
- **getTopFeedByCoin(coin: String)** Get a combined feed (reddit/tweets/articles) for a particular coin (sorted by time)
- **getLatestFeedByCoin(coin: String)** Get a combined feed (reddit/tweets/articles) for a particular coin (sorted by relevance)

The coin slugs are the coin id's used from the CoinMarketCap api. You can see the full list of coins here: [https://api.coinmarketcap.com/v1/ticker/?limit=2000](https://api.coinmarketcap.com/v1/ticker/?limit=2000)

## Sample Response from the API
```javascript
[
    {
        "publishedAt": "2018-05-23T06:30:51.000Z",
        "hotness": 70698.68569444444,
        "activityHotness": 1.6,
        "primaryCategory": "General",
        "words": 302,
        "similarArticles": [
            {
                "publishedAt": "2018-05-23T03:00:05.000Z",
                "_id": "5b04de8d18f173000f9a6d72",
                "title": "PayPal: We’ll ‘Definitely Support’ Bitcoin If It Becomes ‘Better Currency’",
                "url": "https://cryptocontrol.io/r/api/article/5b04de8d18f173000f9a6d72?ref=5ac11440ec0af7be35528459"
            }
        ],
        "coins": [
            {
                "_id": "59cb59e81c073f09e76f614b",
                "name": "Bitcoin",
                "slug": "bitcoin",
                "tradingSymbol": "btc"
            }
        ],
        "_id": "5b07ea76214428000f55a513",
        "description": "Welcome to Crypto Daily™ News, this news piece \"Ripple XRP And Bitcoin Cash Now Live On Revolut\" is breaking news from the Crypto sector.",
        "title": "Ripple XRP And Bitcoin Cash Now Live On Revolut - Crypto Daily™",
        "url": "https://cryptocontrol.io/r/api/article/5b07ea76214428000f55a513?ref=5ac11440ec0af7be35528459",
        "thumbnail": "https://cryptocontrol.io/r/thumbnail/5b07ea76214428000f55a513?ref=5ac11440ec0af7be35528459",
        "originalImageUrl": "https://cryptodaily.co.uk/wp-content/uploads/2018/05/ripple-bitcoincash-credit.jpg"
    }
]
```