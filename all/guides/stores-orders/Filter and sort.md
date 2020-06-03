SortOrder: 1
# Filter and sort

## Query Language

Endpoints that allow querying follow these format [guidelines](https://github.com/wix-private/platformization-guidelines/blob/master/Server/API-Query.md).

## Fields That Allow Filtering

| Field | Operators | Sorting Allowed|
| --- | --- | --- |
| dateCreated |$eq,$ne,$hasSome,$lt,$lte,$gt,$gte|Allowed|
| lastUpdated |$eq,$ne,$hasSome,$lt,$lte,$gt,$gte|Allowed|
| paymentStatus |$eq,$ne,$hasSome|
| archived |$eq,$ne||
| number |$eq,$ne,$hasSome,$lt,$lte,$gt,$gte|Allowed|
| fulfillmentStatus |$eq,$ne,$hasSome|
| id |$eq,$ne,$hasSome|
| lineItems.productId|$eq,$ne,$hasSome,$hasAll| 
| lineItems.name|$eq,$ne,$hasSome,$hasAll|
| billingInfo.address.fullName|$eq,$ne,$hasSome,$contains,$startsWith|
| buyerInfo.id|$eq,$ne,$hasSome|
| channelInfo.type|$eq,$ne,$hasSome|
| enteredBy.id|$eq,$ne,$hasSome|
| channelInfo.externalOrderId|$eq,$ne,$hasSome|

** Note that "HasSome" is same as the operator "IN" in SQL

## Examples

**Get all paid orders**

```
curl 'https://www.wixapis.com/stores/v2/orders/query' --data-binary '{"query":{"filter":"{\"paymentStatus\": \"PAID\"}"}}' -H 'Content-Type: application/json' -H 'Authorization: XXX'
``` 

**Get all orders, sorted by creation time**

```
curl 'https://www.wixapis.com/stores/v2/orders/query' --data-binary '{"query":{"sort":"[{\"dateCreated\": \"asc\"}]"}}' -H 'Content-Type: application/json' -H 'Authorization: XXX'
``` 

**Get orders by ids**

```
curl 'https://www.wixapis.com/stores/v2/orders/query' --data-binary '{"query":{"filter":"{\"id\": {\"$hasSome\": [\"ORDER_ID_1\",\"ORDER_ID_2\"]}}"}}' -H 'Content-Type: application/json' -H 'Authorization: xxx'
``` 