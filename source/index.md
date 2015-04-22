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

> Replace [API_KEY] with the key provided by Vetr:

```shell
$ curl  https://api-prod.vetr.com/api/[API_KEY]/research/getaggregateratings?exchange=NYSE
```

Vetr uses API keys to allow access to the API. You can register for API key contacting us at  [contact@vetr.com](mailto:contact@vetr.com).

Vetr expects for the API key to be included in all API requests to the server and that API is not shared with other users

# APIs

## Security Details

```shell
$ curl  https://api-prod.vetr.com/api/[API_KEY]/research/securityInfo?ticker=NASDAQ:AAPL
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

### HTTP Request

`GET $ https://api-prod.vetr.com/api/[API_KEY]/research/securityInfo?ticker=<ticker>`

Query Parameters

Parameter | Optional | Default | Description
--------- | -------- | ------- | -----------
ticker| false | - | It is a colon separated exchange and ticker EX: NASDAQ:AAPL 

<aside class="notice">
If you do not know the exchange you can skip it and just use ticker EX: APPL. It is always adviced to use exchange to avoid conflicting tickers
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/3"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Isis",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">If you're not using an administrator API key, note that some kittens will return 403 Forbidden if they are hidden for admins only.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the cat to retrieve

