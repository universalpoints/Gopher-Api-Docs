---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - ruby

toc_footers:
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Gopher API! You can use our API to access Hotel API endpoints, which can get rate information for hotels contained in our database.

You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

The Gopher API uses a form of OAuth2.0 for authentication. As of now we only support the [OAuth2.0 Client Crendientials Grant](https://tools.ietf.org/html/rfc6749#section-4.4).

We currently restrict credentials to clients under contract. If you are interested in gaining the proper credentials (`Client Id` and `Client Secret`) please reach out to [our lead developer.](mailto:tommyj@joingopher.com) 

Gopher expects a valid access token to be included in the header of all API requests, like the following:

`Authorization: Bearer VALID_ACCESS_TOKEN`

<aside class="notice">
You must replace <code>VALID_ACCESS_TOKEN</code> with your application's access token.
</aside>

# Hotels

## Get Rates

```ruby
 # TODO add ruby example
```

> The above command returns JSON structured like this:

```json
{
    "checkin_date": "2019-09-03",
    "checkout_date": "2019-09-06",
    "lowest_rate": {
        "avg_price_per_night": 442.3333333333333,
        "subtotal": 1327,
        "cancellable": true,
        "currency": "USD"
    },
    "booking_url": "https://reservations.travelclick.com/6576?datein=09/03/2019&dateout=09/06/2019&hotelid=6576&adults=2",
    "sold_out": false,
    "hotel_error_message": null
}
```

This endpoint retrieves rates for a specific hotel given a set of dates.

### HTTP Request

`GET https://joingopher.com/api/v1/hotels/rates`

### Query Parameters

Parameter | type | Default | Description
--------- | ---- | ------- | -----------
checkin_date | ISO 8601 Date | nil | Date of check in for the rates search
checkout_date | ISO 8601 Date | nil | Date of check out for the rates search
hotel_gid | String | nil | The [Google Place Identifier](https://developers.google.com/places/place-id) for the specific hotel search

