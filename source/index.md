---
title: Vetr API Reference
  
toc_footers:
  - <a href='mailto:contact@vetr.com'>Request for a Developer Key</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to Vetr developer's guide. Vetr is an investment research platform that delivers crowdsourced star ratings for stocks and provides access to investment insights from trusted sources for self-driven investors. Vetr provides simple REST API's to get aggregated ratings of the crowd and other information related to securities. They are easy to use and integrate all you need is the api key

# How to use

> Replace \<API_KEY\> with the key provided by Vetr:

```shell
$ curl  https://vetr-prod.apigee.net/v1/api/research/getaggregateratings?exchange=NASDAQ&apikey=<API_KEY>
```

Vetr uses API keys to allow access to the API. You can register for API key contacting us at  [contact@vetr.com](mailto:contact@vetr.com).

Vetr expects for the API key to be included in all API requests to the server and that API is not shared with other users

# APIs

## Security Details

```shell
$ curl  https://vetr-prod.apigee.net/v1/api/research/securityInfo?ticker=NASDAQ:AAPL&apikey=<API_KEY> 
```
>Response:

```json
{
  "data": {
    "security": {
      "securityMasterId": 4275,
      "ticker": "AAPL",
      "company": "Apple Inc",
      "exchange": "NASDAQ",
      "securityWallId": 4275,
      "fullTicker": "NASDAQ:AAPL",
      "resultScore": 0,
      "secType": null,
      "remark": null,
      "active": true
    },
    "heldByCount": 406,
    "financialhighlights": {
      "symbol": "AAPL",
      "marketCapitalization": 738869248000,
      "insiderShareholders": 0.0007,
      "annualRevenue": 199800,
      "ttmRevenue": 148812000000,
      "sharesOutstanding": 5824750,
      "institutionalShareholders": 60.540001,
      "oneYearReturn": 73.92,
      "threeYearReturn": 66.27,
      "fiveYearReturn": 278.83,
      "ttmRevenueGrowth": 148812000000,
      "fiveYearRevenueGrowth": 180.25,
      "fiveYearEarningsGrowth": 198.61,
      "fiveYearDividendGrowth": 0,
      "annualEPS": 7.42,
      "annualDividendRate": 1.88,
      "annualDividendYield": 1.49
    },
    "aggratingcalc": {
      "securityMasterId": 4275,
      "ratingComputeDate": "2015-04-22",
      "aggRatingScore": 3.2564102564102564,
      "totalRatings": 78,
      "bullishCount": 45,
      "bearishCount": 33,
      "totalBuys": 38,
      "totalSells": 28,
      "totalHolds": 12,
      "avg3mTarget": 129.07035714285715,
      "avg3mTargetPct": 0.017022749530038225,
      "avg6mTarget": 134.95529411764704,
      "avg6mTargetPct": 0.06339369724723856,
      "avg9mTarget": 0,
      "avg9mTargetPct": 0,
      "avg12mTarget": 0,
      "avg12mTargetPct": 0,
      "currentPrice": 126.91,
      "direction": "no",
      "prev_score": 3.2564102564102564,
      "valid": true
    },
    "companyProfile": {
      "symbol": "AAPL",
      "exchange": "NASDAQ",
      "exchangeName": "Apple Inc",
      "sicSector": "3571",
      "industry": "Computer",
      "subIndustry": "Mini",
      "businessSummary": "Apple Inc. is engaged in designing, manufacturing and marketing mobile communication and media devices, personal computers, and portable digital music players. The Company's products and services include iPhone, iPad, Mac, iPod, Apple TV, a portfolio of consumer and professional software applications, the iOS and Mac OS X operating systems, iCloud, and a range of accessory, service and support offerings. It sells its products worldwide through its online stores, its retail stores, its direct sales force, third-party wholesalers, and resellers. Apple Inc. is headquartered in Cupertino, California.",
      "ceo": "Timothy D. Cook",
      "address": "ONE INFINITE LOOP",
      "city": "CUPERTINO",
      "state": "CA",
      "zipCode": "95014",
      "phoneNumber": "408-996-1010"
    }
  },
  "success": true,
  "errorMessage": "",
  "totalRecords": -1,
  "hasMore": false,
  "sgn": false
}
```


This endpoint retrieves all the details of a particular ticker.

HTTP Request

`GET https://vetr-prod.apigee.net/v1/api/research/securityInfo?ticker=<ticker>&apikey=<API_KEY>`

Query Parameters

Parameter | Optional | Default | Description
--------- | -------- | ------- | -----------
ticker| No | - | It is a colon separated exchange and ticker EX: NASDAQ:AAPL 


Example Request/Response

* [Example to get security details](https://www.hurl.it/?url=https://vetr-prod.apigee.net/v1/api/research/securityInfo&method=GET&args={%22apikey%22:[%22[Enter%20your%20API%20KEY%20here]%22],%22ticker%22:[%22NASDAQ:AAPL%22]}) 


<aside class="notice">
If you do not know the exchange you can skip it and just use ticker EX: APPL. It is always adviced to use exchange to avoid conflicting tickers
</aside>

## Ratings of User


```shell
$ curl  https://vetr-prod.apigee.net/v1/api/recommendations/ratings/Santosh-Kn?start=0&limit=4&apikey=<API_KEY> 
```

>Response:

```json
{
  "data": [
    {
      "security": {
        "securityMasterId": 9144,
        "ticker": "AAP",
        "company": "Advance Auto Parts Inc",
        "exchange": "NYSE",
        "securityWallId": 9144,
        "fullTicker": "NYSE:AAP",
        "resultScore": 0,
        "secType": null,
        "remark": null,
        "active": true
      },
      "count": 1,
      "latestRecommendationSummary": null,
      "activeRecommendationSummary": {
        "postUid": "4915442010-agfinancialmgt-shared-a-chart-on-StockTwits",
        "recommendationId": 16300,
        "createdOn": "2014-11-05T20:21:46.998Z",
        "rating": "BULLISH",
        "ratingTitle": "agfinancialmgt shared a chart on StockTwits",
        "securityMasterId": 9144,
        "securityWallId": 9144,
        "issuePrice": 149.52000427246094,
        "targetPrice": 169,
        "expiryDate": "2015-11-05T05:00:00.000Z",
        "expiryTimeFrame": "1Y",
        "pctToTarget": 0.1154379248894463,
        "ratingScore": 4,
        "returnPct": 0.013
      }
    },
    {
      "security": {
        "securityMasterId": 4275,
        "ticker": "AAPL",
        "company": "Apple Inc",
        "exchange": "NASDAQ",
        "securityWallId": 4275,
        "fullTicker": "NASDAQ:AAPL",
        "resultScore": 0,
        "secType": null,
        "remark": null,
        "active": true
      },
      "count": 1,
      "latestRecommendationSummary": null,
      "activeRecommendationSummary": {
        "postUid": "7910697854",
        "recommendationId": 22046,
        "createdOn": "2015-01-27T20:19:37.225Z",
        "rating": "BULLISH",
        "ratingTitle": "",
        "securityMasterId": 4275,
        "securityWallId": 4275,
        "issuePrice": 111.19999694824219,
        "targetPrice": 117,
        "expiryDate": "2015-04-27T04:00:00.000Z",
        "expiryTimeFrame": "3M",
        "pctToTarget": -0.09034364795521695,
        "ratingScore": 1.5,
        "returnPct": 0.157
      }
    },
    {
      "security": {
        "securityMasterId": 53535,
        "ticker": "AAVL",
        "company": "Avalanche Biotechnologies Inc.",
        "exchange": "NASDAQ",
        "securityWallId": 53535,
        "fullTicker": "NASDAQ:AAVL",
        "resultScore": 0,
        "secType": null,
        "remark": null,
        "active": true
      },
      "count": 1,
      "latestRecommendationSummary": null,
      "activeRecommendationSummary": {
        "postUid": "7373739041",
        "recommendationId": 22981,
        "createdOn": "2015-02-09T15:10:56.484Z",
        "rating": "BULLISH",
        "ratingTitle": "",
        "securityMasterId": 53535,
        "securityWallId": 53535,
        "issuePrice": 33.869998931884766,
        "targetPrice": 39,
        "expiryDate": "2015-08-09T04:00:00.000Z",
        "expiryTimeFrame": "6M",
        "pctToTarget": 0.0017980991523246926,
        "ratingScore": 3,
        "returnPct": 0.149
      }
    },
    {
      "security": {
        "securityMasterId": 4278,
        "ticker": "ABAX",
        "company": "Abaxis Inc",
        "exchange": "NASDAQ",
        "securityWallId": 4278,
        "fullTicker": "NASDAQ:ABAX",
        "resultScore": 0,
        "secType": null,
        "remark": null,
        "active": true
      },
      "count": 1,
      "latestRecommendationSummary": null,
      "activeRecommendationSummary": {
        "postUid": "2449661116",
        "recommendationId": 23813,
        "createdOn": "2015-02-20T19:54:41.722Z",
        "rating": "BULLISH",
        "ratingTitle": "",
        "securityMasterId": 4278,
        "securityWallId": 4278,
        "issuePrice": 60.310001373291016,
        "targetPrice": 68,
        "expiryDate": "2015-08-20T04:00:00.000Z",
        "expiryTimeFrame": "6M",
        "pctToTarget": 0.07509881422924901,
        "ratingScore": 4,
        "returnPct": 0.049
      }
    }
  ],
  "success": true,
  "errorMessage": "",
  "totalRecords": -1,
  "hasMore": false,
  "sgn": false
}
```

This endpoint retrieves all the recommendations of a particular user

HTTP Request:

`GET https://vetr-prod.apigee.net/v1/api/recommendations/ratings/[ProfileSlug]?start=<start>&limit=<limit>&apikey=<API_KEY>`

Url Parameters:

Parameter | Optional | Default | Description
--------- | -------- | ------- | -----------
ProfileSlug| No | - | profile handler/slug of the user whoes ratings are needed 
start| Yes | 0 | Starting index of the ratings (Index starts from 0) 
limit| Yes | 50 | Limit the number of ratings returned from the starting index  



Example Request/Response

* [Example to get ratings of a particular user](https://www.hurl.it/?url=https://vetr-prod.apigee.net/v1/api/recommendations/ratings/[ProfileSlug]&method=GET&args={%22apikey%22:[%22[Enter%20your%20API%20KEY%20here]%22],%22start%22:[%220%22],%22limit%22:[%2210%22]})  (replace [ProfileSlug] in URL and enter the API_KEY) 


## Ratings of User for a security


```shell
$ curl  https://vetr-prod.apigee.net/v1/api/recommendations/ratings/Santosh-Kn/NASDAQ:AAPL?apikey=<API_KEY> 
```

>Response:

```json
{
  "data": [
    {
      "postUid": "QGPYBEguPQgzSC",
      "recommendationId": 12757,
      "createdOn": "2014-09-17T19:56:08.723Z",
      "rating": "BULLISH",
      "ratingTitle": "Apple iPhone 6 pre-orders hit record 4 million on first day",
      "securityMasterId": 4275,
      "securityWallId": 4275,
      "issuePrice": 101.27999877929688,
      "targetPrice": 120,
      "expiryDate": "2014-12-17T05:00:00.000Z",
      "expiryTimeFrame": "3M",
      "pctToTarget": 0.1111111111111111,
      "ratingScore": 4.5,
      "returnPct": 0.066
    },
    {
      "postUid": "7407207951",
      "recommendationId": 16673,
      "createdOn": "2014-11-11T18:47:24.144Z",
      "rating": "BULLISH",
      "ratingTitle": "",
      "securityMasterId": 4275,
      "securityWallId": 4275,
      "issuePrice": 108.8499984741211,
      "targetPrice": 115,
      "expiryDate": "2015-02-11T05:00:00.000Z",
      "expiryTimeFrame": "3M",
      "pctToTarget": -0.09062154040803412,
      "ratingScore": 1.5,
      "returnPct": 0.162
    },
    {
      "postUid": "4086059908",
      "recommendationId": 23638,
      "createdOn": "2015-02-18T19:02:45.857Z",
      "rating": "BEARISH",
      "ratingTitle": "",
      "securityMasterId": 4275,
      "securityWallId": 4275,
      "issuePrice": 127.70999908447266,
      "targetPrice": 120,
      "expiryDate": "2015-05-18T04:00:00.000Z",
      "expiryTimeFrame": "3M",
      "pctToTarget": -0.07535829865926955,
      "ratingScore": 2,
      "returnPct": -0.016
    }
  ],
  "success": true,
  "errorMessage": "",
  "totalRecords": -1,
  "hasMore": false,
  "sgn": false
}
```

This endpoint retrieves all the recommendations of a particular user for a particular ticker

HTTP Request:

`GET https://vetr-prod.apigee.net/v1/api/recommendations/ratings/[ProfileSlug]/[ticker]?apikey=<API_KEY>`

URL Parameters:

Parameter | Optional | Default | Description
--------- | -------- | ------- | -----------
ProfileSlug| No | - | profile handler/slug of the user whoes ratings are needed 
ticker| No | - | It is a colon separated exchange and ticker EX: NASDAQ:AAPL 

Example Request/Response:

* [Example to get ratings of a particular user](https://www.hurl.it/?url=https://vetr-prod.apigee.net/v1/api/recommendations/ratings/[ProfileSlug]/[ticker]&method=GET&args={%22apikey%22:[%22[Enter%20your%20API%20KEY%20here]%22]})  (replace [ProfileSlug] and [ticker] in URL and enter the API_KEY) 

## Posts Of Ticker

```shell

$ curl https://vetr-prod.apigee.net/v1/api/posts/ticker?ticker=NASDAQ:AAPL&sortBy=post_id:desc&show=all&ratingsFilter=active_only&fullText=false&start=12&limit=14&apikey=<API_KEY>

```

>Response 

```json
{
  "data": [
    {
      "postUid": "3729288021",
      "postType": "RECOMMENDATION",
      "visibility": "PUBLIC",
      "entryId": "recommendation:27752",
      "publishedToProfileSlug": "mitchgettingrich",
      "ownerProfileSlug": "mitchgettingrich",
      "score": 0,
      "commentCount": 0,
      "securityMasterId": 4275,
      "securityWallId": 4275,
      "shortUrl": "http://go.vetr.com/1yIbA7z",
      "importedAnalystRating": false,
      "recommendationId": 27752,
      "targetPrice": 180,
      "issuePrice": 125.55,
      "expiryPrice": 0,
      "exchange": "NASDAQ",
      "ticker": "NASDAQ:AAPL",
      "issueDate": "2015-04-19",
      "targetDate": "2015-10-19",
      "createdDateTime": "2015-04-19T16:44:36.322Z",
      "targetTimeFrame": "6M",
      "rating": "BULLISH",
      "ratingTitle": "",
      "commentary": "",
      "company": "Apple Inc",
      "issuedByProfile": {
        "profileType": "MEMBER",
        "profileName": "mitchgettingrich",
        "profileTitle": "Day and Swing Trading",
        "profilePictureUrl": "https://s3.amazonaws.com/whisperinvest-images/default.png",
        "connectionMemberId": 1160,
        "connectionPageId": 0,
        "profileSlug": "mitchgettingrich",
        "profileSlugAlias": "mitchgettingrich",
        "isVerified": false,
        "ratingsCount": 0,
        "subscriberCount": 8,
        "contributesToPages": [],
        "unClaimed": false
      },
      "ownerProfile": {
        "profileType": "MEMBER",
        "profileName": "mitchgettingrich",
        "profileTitle": "Day and Swing Trading",
        "profilePictureUrl": "https://s3.amazonaws.com/whisperinvest-images/default.png",
        "connectionMemberId": 1160,
        "connectionPageId": 0,
        "profileSlug": "mitchgettingrich",
        "profileSlugAlias": "mitchgettingrich",
        "isVerified": false,
        "ratingsCount": 0,
        "subscriberCount": 0,
        "contributesToPages": [],
        "unClaimed": false
      },
      "priorRatingId": 0,
      "nextRatingId": 0,
      "targetPriceReached": false,
      "ratingCalc": {
        "recommendationRatingId": null,
        "ratingComputeDate": "2015-04-23",
        "ratingScore": 5,
        "pctToTarget": 0.3869625520110957,
        "returnPct": 0.034,
        "lastMarketPrice": 129.78,
        "targetPriceReached": false,
        "targetPriceOff": false
      },
      "likedByMe": false,
      "downVotedByMe": false,
      "allowEdit": false,
      "relatedTickers": [],
      "contestEntry": false,
      "viewCount": 0,
      "closed": false,
      "expired": false,
      "active": true,
      "long": false
    },
    {
      "postUid": "0180160778-Notable-Initiations-Apple-AAPL-Plug-Power-PLUG-CyberArk-CYBR-FuelCell-Energy",
      "postType": "ARTICLE",
      "visibility": "PUBLIC",
      "entryId": "article:106796",
      "publishedToProfileSlug": "Wall-Street-Pit",
      "ownerProfileSlug": "Investing-Channel",
      "score": 0,
      "commentCount": 0,
      "externalSourceId": "Investing-Channel:http://wallstreetpit.com/107950-notable-initiations-apple-aapl-plug-power-plug-cyberark-cybr-fuelcell-energy-fcel-cytrx-cytr/",
      "shortUrl": "http://go.vetr.com/1Jc4XdI",
      "importedAnalystRating": false,
      "ratingAction": null,
      "analystRating": null,
      "attachments": null,
      "articleId": 106796,
      "issuedByMemberId": 387,
      "securityMasterId": 0,
      "securityWallId": 4275,
      "ticker": null,
      "company": null,
      "articleType": "TEXT",
      "articleTitle": "Notable Initiations: Apple  $AAPL, Plug Power  $PLUG, CyberArk  $CYBR, FuelCell Energy  $FCEL, CytRx  $CYTR",
      "articleText": "<p>In a report published Friday, FBR Capital analysts initiated coverage on Apple Inc.  <a href=\"/research/NASDAQ:AAPL\" analytics-on=\"click\" analytics-category=\"outbound\" analytics-event=\"url\" analytics-label=\"/research/NASDAQ:AAPL\">$AAPL</a> with a 'Outperform' rating and $185 price target. On valuation measures, Apple Inc. shares currently have a PEG and forward P/E ratio of 1.10 and 13.35, respectively. Price/sales for the same period is 3.68 while EPS is $7.39.</p>\n",
      "articleUrl": "http://wallstreetpit.com/107950-notable-initiations-apple-aapl-plug-power-plug-cyberark-cybr-fuelcell-energy-fcel-cytrx-cytr/",
      "embedInfo": {
        "provider_url": "http://wallstreetpit.com",
        "height": 0,
        "width": 0,
        "provider_name": "Wall Street Pit",
        "type": "link",
        "title": "Notable Initiations: Apple (AAPL), Plug Power (PLUG), CyberArk (CYBR), FuelCell Energy (FCEL), CytRx (CYTR)",
        "author_name": "WSP",
        "author_url": "http://wallstreetpit.com/author/editor/",
        "description": "In a report published Friday, FBR Capital analysts initiated coverage on Apple Inc. (AAPL) with a 'Outperform' rating and $185 price target. On valuation measures, Apple Inc. shares currently have a PEG and forward P/E ratio of 1.10 and 13.35, respectively. Price/sales for the same period is 3.68 while EPS is $7.39.",
        "thumbnail_url": "/imgproxyCrop?url=http%3A%2F%2Fwallstreetpit.com%2Fwp-content%2Fthemes%2Fmain_theme%2Fsociable%2Ffb-logo-250x250.jpg",
        "thumbnail_width": 250,
        "thumbnail_height": 250,
        "url": "http://wallstreetpit.com/107950-notable-initiations-apple-aapl-plug-power-plug-cyberark-cybr-fuelcell-energy-fcel-cytrx-cytr/"
      },
      "relatedTickers": [
        "NASDAQ:AAPL",
        "NASDAQ:CYTR",
        "NASDAQ:FCEL",
        "NASDAQ:PLUG",
        "NASDAQ:CYBR"
      ],
      "relatedSecMasterIds": null,
      "issuedByProfile": {
        "profileType": "PAGE",
        "profileName": "Wall Street Pit",
        "profileDescription": "Wall Street Pit is a financial news and opinion website covering the economy, markets and global finance.",
        "profilePictureUrl": "https://s3.amazonaws.com/assets-prod.whisperinvest.com/profile-pics/Wall-Street-Pit/normal.png",
        "profileWebLink": "http://wallstreetpit.com/",
        "connectionMemberId": 0,
        "connectionPageId": 356,
        "profileSlug": "Wall-Street-Pit",
        "profileSlugAlias": "Wall-Street-Pit",
        "isVerified": false,
        "ratingsCount": 0,
        "subscriberCount": 19,
        "contributesToPages": [],
        "unClaimed": true
      },
      "ownerProfile": {
        "profileType": "MEMBER",
        "profileName": "Investing Channel",
        "profileDescription": "",
        "profilePictureUrl": "https://s3.amazonaws.com/whisperinvest-images/default.png",
        "connectionMemberId": 387,
        "connectionPageId": 0,
        "profileSlug": "Investing-Channel",
        "profileSlugAlias": "Investing-Channel",
        "isVerified": false,
        "ratingsCount": 0,
        "subscriberCount": 0,
        "contributesToPages": [],
        "unClaimed": false
      },
      "likedByMe": false,
      "likedBy": null,
      "downVotedByMe": false,
      "downVotedBy": null,
      "allowEdit": false,
      "viewCount": 0,
      "createdDateTime": "2015-04-17T19:41:24.154Z",
      "active": true,
      "long": false
    }
  ],
  "success": true,
  "errorMessage": "",
  "totalRecords": 0,
  "hasMore": true,
  "sgn": false
}

```

This endpoint returns all the posts realted to a ticker.




HTTP Request:


`GET https://vetr-prod.apigee.net/v1/api/posts/ticker?ticker=<ticker>&sortBy=<sortBy>&show=<show>&ratingsFilter=<ratingsFilter>&fullText=<fullText>&start=<start>&limit=<limit>&apikey=<API_KEY>`



URL Parameters:

Parameter | Optional | Default | Description
--------- | -------- | ------- | -----------
ticker | No | - | It is a colon separated exchange and ticker EX: NASDAQ:AAPL 
sortBy | Yes | popular | Specifiy the order in which records are sorted [More deatils below this table]
show | Yes | all | Specifiy whether to display only posts ('posts_only') or only ratings('ratings_only') or both('all')
ratingsFilter| Yes | active_only | Spicifies filter for rating [More deatils below this table]
fullText | Yes | false | Specifies whether to fetch full text of article('true') or summary only('false')
start| Yes | 0 | Starting index of the post (Index starts from 0) 
limit| Yes | 10 | Limit here indicates the end of index EX:start=7&limit=10 then it fetches posts 7,8 and 9

* sortBy:

Value | Description | Restriction
----- | ----------- | -----------
popular | sort based on popularity | -
created_on:asc | sort based on creation date of posts in ascending order | -
created_on:desc | sort based on creation date of posts in descending order | -
recommendation_id:asc | sort based on creation date of ratings in ascending order | to be used only with show=ratings_only
recommendation_id:desc | sort based on creation date of ratings in descending order | to be used only with show=ratings_only
rating_score:asc | Lowest rated first | to be used only with show=ratings_only
rating_score:desc | Highest rated first | to be used only with show=ratings_only
target_price:asc | Lowest target price first | to be used only with show=ratings_only
target_price:desc | Highest target price first | to be used only with show=ratings_only
expiry_date:asc | Earliest Expiration first | to be used only with show=ratings_only
expiry_date:desc | Latest Expiration first | to be used only with show=ratings_only

* ratingsFilter

Value | Description 
----- | -----------
active_only | Include active ratings only which is neither closed nor expired
past_only | Include ratings that are either closed or expired
bullish_only | Include ratings which are active and also Bullish
bearish_only | Include ratings which are active and also Bearish


Example Request/Response:
//https://vetr-prod.apigee.net/v1/api/posts/ticker?ticker=<ticker>&sortBy=<sortBy>&show=<show>&ratingsFilter=<ratingsFilter>&fullText=<fullText>&start=<start>&limit=<limit>&apikey=<API_KEY>

* [Example to get top 10 posts related to NASDAQ:AAPL](https://www.hurl.it/?url=https://vetr-prod.apigee.net/v1/api/posts/ticker&method=GET&args={%22apikey%22:[%22[Enter%20your%20API%20KEY%20here]%22],%22ticker%22:[%22NASDAQ:AAPL%22]}) 

* [Example to get latest bullish ratings for NASDAQ:AAPL](https://www.hurl.it/?url=https://vetr-prod.apigee.net/v1/api/posts/ticker&method=GET&args={%22apikey%22:[%22[Enter%20your%20API%20KEY%20here]%22],%22ticker%22:[%22NASDAQ:AAPL%22],%22show%22:[%22ratings_only%22],%22ratingsFilter%22:[%22bullish_only%22],%22sortBy%22:[%22recommendation_id:desc%22]})  
