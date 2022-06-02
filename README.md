# Actor - Total Wine & More Scraper

[APIFY Link](https://apify.com/oyildirim/totalwine-actor)

## Total Wine & More scraper

Since Total Wine & More doesn't provide a good and free API, this actor should help you to retrieve data from it.

The Total Wine & More data scraper supports the following features:

-   Search any keyword - You can search any keyword you would like to have and get the results

-   Scrape lists - Scrape any list that you'd like to get from Total Wine & More

## Bugs, fixes, updates and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/onurburak9/totalwine-crawler/issues).

## Setup & Usage

User has to enter a search keyword or a start URL to use the scraper. Currently, actor only support product lists URLs as the startURL The scraper needs to be used with an US-based proxy.

### Using Search

- User can enter a single `search term` and set maxItems/endPage if wanted
- Actor iterates through all pages of the search result until all conditions are satisfied

You can check the output of this example [here](https://api.apify.com/v2/datasets/dxKQK1WeufFpbkIMN/items?clean=true&format=json).
#### Input
```json
{
  "maxItems": 25,
  "endPage": 3,
  "proxy": {
    "useApifyProxy": true,
    "apifyProxyCountry": "US"
  },
  "search": "sparkling"
}
```

### Using Start URLs

- User can enter any number of startURLs maxItems/endPage if wanted
- For every URL, actor parses the products listed and also iterates through succeding pages per startURL given

You can check the output of this example [here](https://api.apify.com/v2/datasets/cbl6BWY46rcp7blm0/items?clean=true&format=json).
#### Input
```json
{
  "maxItems": 48,
  "endPage": 5,
  "proxy": {
    "useApifyProxy": true,
    "apifyProxyCountry": "US"
  },
  "startUrls": [
    "https://www.totalwine.com/wine/red-wine/c/000009"
  ]
}
```

## Input Parameters

The input of this scraper should be JSON containing the list of pages on Total Wine & More that should be visited. Required fields are:

| Field                | Type    | Description                                                                                                                                                                                                    |
| -------------------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| search               | String  | (optional) Keyword that you want to search on Total Wine & More.                                                                                                                                                       |
| startUrls            | Array   | (optional) List of Total Wine & More URLs. You should only provide product list URLs                                                                                                                 |
| endPage              | Integer | (optional) Final number of page that you want to scrape. Default is `Infinite`. This is applies to all `search` request and `startUrls` individually.                                                          |
| maxItems             | Integer | (optional) You can limit scraped products. This should be useful when you search through the big subcategories.                                                                                                |
| proxy                | Object  | Proxy configuration                                                                                                                                                                                            |
| extendOutputFunction | String  | (optional) Function that takes a JQuery handle ($) as argument and returns object with data                                                                                                                    |
| customMapFunction | String  | (optional) Function that takes each objects handle as argument and returns object with executing the function                                                                                                                     |

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

##### Tip

When you want to have a scrape over a specific listing URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.

### Total Wine & More Scraper input example

```json
{
    "startUrls": [

    ],
    "proxy": {
        "useApifyProxy": true,
        "apifyProxyCountry": "US"
    },
    "endPage": 5,
    "maxItems": 100
}
```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## Total Wine & More Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Total Wine & More actor.

## Scraped Total Wine & More Properties

The structure of each item in Total Wine & More looks like this:

### Item Detail

```json
{
  "bay": "",
  "brand": {
    "id": "Mascota Vineyards",
    "name": "Mascota Vineyards"
  },
  "categories": [
    {
      "id": "000284",
      "name": "Mendoza",
      "type": "REGION",
      "url": "https://www.totalwine.com/wine/argentina/mendoza/c/000284",
      "storefrontUrl": "/wine/argentina/mendoza/c/000284"
    },
    {
      "id": "000009",
      "name": "Red Wine",
      "type": "PRODUCT_TYPE",
      "url": "https://www.totalwine.com/wine/red-wine/c/000009",
      "storefrontUrl": "/wine/red-wine/c/000009"
    },
    {
      "id": "000011",
      "name": "Cabernet Sauvignon",
      "type": "VARIETAL_TYPE",
      "url": "https://www.totalwine.com/wine/red-wine/cabernet-sauvignon/c/000011",
      "storefrontUrl": "/wine/red-wine/cabernet-sauvignon/c/000011"
    }
  ],
  "containerType": "Bottle",
  "customerAverageRating": 4.4,
  "customerReviewsCount": 998,
  "department": "c0020",
  "directType": "Winery Direct",
  "id": "130007750",
  "images": [
    {
      "imageType": "DEFAULT",
      "mobileOptimizedUrl": "https://www.totalwine.com/media/sys_master/twmmedia/h72/h2e/15949509165086.png",
      "thumbnailUrl": "https://www.totalwine.com/media/sys_master/twmmedia/h72/h2e/15949509165086.png",
      "url": "https://www.totalwine.com/media/sys_master/twmmedia/h72/h2e/15949509165086.png",
      "zoomImageUrl": "https://www.totalwine.com/media/sys_master/twmmedia/h72/h2e/15949509165086.png",
      "altText": "Mascota Vineyards Unanime, 2017"
    }
  ],
  "location": "Aisle 02, Left",
  "name": "Mascota Vineyards Unanime, 2017",
  "packageDescription": "750ml",
  "packageValue": "Single",
  "price": [
    {
      "price": 25.99,
      "type": "EDLP"
    },
    {
      "price": 19.99,
      "type": "LTSP"
    }
  ],
  "productUrl": "/wine/gift-center/deals/red-wine/cabernet-sauvignon/mascota-vineyards-unanime/p/130007750",
  "review": "James Suckling-Mendoza, Argentina - \"This is a rich, dense red with blackberry and blueberry aromas and flavors. Extremely well-crafted tannins. Hints of vanilla to the ripe fruit at the end. Incredible value...already beautiful to taste.\"",
  "rating": 95,
  "ratingSource": "James Suckling",
  "salesStrategy": {
    "name": "Winery Direct"
  },
  "shoppingOptions": [
    {
      "eligible": false,
      "location": "US-TX",
      "message": [
        "Unavailable"
      ],
      "type": "SHIPPING",
      "selected": false
    },
    {
      "eligible": true,
      "location": "Oak Lawn, TX",
      "type": "INSTORE_PICKUP",
      "selected": true
    },
    {
      "eligible": true,
      "location": "Oak Lawn, TX",
      "type": "DELIVERY",
      "selected": false
    }
  ],
  "skuId": "130007750-1",
  "stockLevel": [
    {
      "purchaseLimit": 6,
      "stock": 211
    }
  ],
  "storeDistance": 0.0001798902,
  "storeId": "531",
  "storeName": "Oak Lawn",
  "itemTasteProfile": "Blackberry, Chocolate",
  "itemStyle": "Elegant",
  "itemBody": "Full-bodied",
  "transactional": true,
  "type": "PRODUCT",
  "volume": "",
  "stockMessages": {
    "messages": [
      {
        "shoppingMethod": "INSTORE_PICKUP",
        "stockMessage": "In stock",
        "addToCartMessage": "Add to cart",
        "addToCartStatus": true
      },
      {
        "shoppingMethod": "DELIVERY",
        "stockMessage": "Available",
        "addToCartMessage": "Add to cart",
        "addToCartStatus": true
      },
      {
        "shoppingMethod": "SHIPPING",
        "stockMessage": "Unavailable",
        "addToCartMessage": "View Product",
        "addToCartStatus": false
      }
    ],
    "digitalTransactional": true,
    "digitalInventoryQuantity": 211,
    "digitalSpecialOrder": false,
    "digitalLongTermOOS": false,
    "digitalLimitedStock": false,
    "digitalInStock": true,
    "digitalStoreQuantity": 213,
    "shippingTransactional": false,
    "shippingInventoryQuantity": 211,
    "shippingSpecialOrder": false,
    "shippingLongTermOOS": false,
    "shippingLimitedStock": false,
    "shippingInStock": true,
    "shippingStoreQuantity": 213,
    "digitalDeliveryEligible": true
  }
}
```
