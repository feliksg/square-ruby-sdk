# Gift Cards

```ruby
gift_cards_api = client.gift_cards
```

## Class Name

`GiftCardsApi`

## Methods

* [List Gift Cards](/doc/api/gift-cards.md#list-gift-cards)
* [Create Gift Card](/doc/api/gift-cards.md#create-gift-card)
* [Retrieve Gift Card From GAN](/doc/api/gift-cards.md#retrieve-gift-card-from-gan)
* [Retrieve Gift Card From Nonce](/doc/api/gift-cards.md#retrieve-gift-card-from-nonce)
* [Link Customer to Gift Card](/doc/api/gift-cards.md#link-customer-to-gift-card)
* [Unlink Customer From Gift Card](/doc/api/gift-cards.md#unlink-customer-from-gift-card)
* [Retrieve Gift Card](/doc/api/gift-cards.md#retrieve-gift-card)


# List Gift Cards

Lists all gift cards. You can specify optional filters to retrieve
a subset of the gift cards.

```ruby
def list_gift_cards(type: nil,
                    state: nil,
                    limit: nil,
                    cursor: nil,
                    customer_id: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `type` | `String` | Query, Optional | If a type is provided, gift cards of this type are returned<br>(see [GiftCardType](/doc/models/gift-card-type.md)).<br>If no type is provided, it returns gift cards of all types. |
| `state` | `String` | Query, Optional | If the state is provided, it returns the gift cards in the specified state<br>(see [GiftCardStatus](/doc/models/gift-card-status.md)).<br>Otherwise, it returns the gift cards of all states. |
| `limit` | `Integer` | Query, Optional | If a value is provided, it returns only that number of results per page.<br>The maximum number of results allowed per page is 50. The default value is 30. |
| `cursor` | `String` | Query, Optional | A pagination cursor returned by a previous call to this endpoint.<br>Provide this cursor to retrieve the next set of results for the original query.<br>If a cursor is not provided, it returns the first page of the results.<br>For more information, see [Pagination](https://developer.squareup.com/docs/working-with-apis/pagination). |
| `customer_id` | `String` | Query, Optional | If a value is provided, returns only the gift cards linked to the specified customer |

## Response Type

[`List Gift Cards Response Hash`](/doc/models/list-gift-cards-response.md)

## Example Usage

```ruby
type = 'type0'
state = 'state4'
limit = 172
cursor = 'cursor6'
customer_id = 'customer_id8'

result = gift_cards_api.list_gift_cards(type: type, state: state, limit: limit, cursor: cursor, customer_id: customer_id)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Create Gift Card

Creates a digital gift card or registers a physical (plastic) gift card. You must activate the gift card before
it can be used for payment. For more information, see
[Selling gift cards](https://developer.squareup.com/docs/gift-cards/using-gift-cards-api#selling-square-gift-cards).

```ruby
def create_gift_card(body:)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`Create Gift Card Request Hash`](/doc/models/create-gift-card-request.md) | Body, Required | An object containing the fields to POST for the request.<br><br>See the corresponding object definition for field details. |

## Response Type

[`Create Gift Card Response Hash`](/doc/models/create-gift-card-response.md)

## Example Usage

```ruby
body = {}
body[:idempotency_key] = 'NC9Tm69EjbjtConu'
body[:location_id] = '81FN9BNFZTKS4'
body[:gift_card] = {}
body[:gift_card][:id] = 'id4'
body[:gift_card][:type] = 'DIGITAL'
body[:gift_card][:gan_source] = 'SQUARE'
body[:gift_card][:state] = 'ACTIVE'
body[:gift_card][:balance_money] = {}
body[:gift_card][:balance_money][:amount] = 2
body[:gift_card][:balance_money][:currency] = 'DOP'
body[:gift_card][:gan] = 'gan0'

result = gift_cards_api.create_gift_card(body: body)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Retrieve Gift Card From GAN

Retrieves a gift card using the gift card account number (GAN).

```ruby
def retrieve_gift_card_from_gan(body:)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`Retrieve Gift Card From GAN Request Hash`](/doc/models/retrieve-gift-card-from-gan-request.md) | Body, Required | An object containing the fields to POST for the request.<br><br>See the corresponding object definition for field details. |

## Response Type

[`Retrieve Gift Card From GAN Response Hash`](/doc/models/retrieve-gift-card-from-gan-response.md)

## Example Usage

```ruby
body = {}
body[:gan] = '7783320001001635'

result = gift_cards_api.retrieve_gift_card_from_gan(body: body)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Retrieve Gift Card From Nonce

Retrieves a gift card using a nonce (a secure token) that represents the gift card.

```ruby
def retrieve_gift_card_from_nonce(body:)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`Retrieve Gift Card From Nonce Request Hash`](/doc/models/retrieve-gift-card-from-nonce-request.md) | Body, Required | An object containing the fields to POST for the request.<br><br>See the corresponding object definition for field details. |

## Response Type

[`Retrieve Gift Card From Nonce Response Hash`](/doc/models/retrieve-gift-card-from-nonce-response.md)

## Example Usage

```ruby
body = {}
body[:nonce] = 'cnon:7783322135245171'

result = gift_cards_api.retrieve_gift_card_from_nonce(body: body)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Link Customer to Gift Card

Links a customer to a gift card

```ruby
def link_customer_to_gift_card(gift_card_id:,
                               body:)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `gift_card_id` | `String` | Template, Required | The ID of the gift card to link. |
| `body` | [`Link Customer to Gift Card Request Hash`](/doc/models/link-customer-to-gift-card-request.md) | Body, Required | An object containing the fields to POST for the request.<br><br>See the corresponding object definition for field details. |

## Response Type

[`Link Customer to Gift Card Response Hash`](/doc/models/link-customer-to-gift-card-response.md)

## Example Usage

```ruby
gift_card_id = 'gift_card_id8'
body = {}
body[:customer_id] = 'GKY0FZ3V717AH8Q2D821PNT2ZW'

result = gift_cards_api.link_customer_to_gift_card(gift_card_id: gift_card_id, body: body)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Unlink Customer From Gift Card

Unlinks a customer from a gift card

```ruby
def unlink_customer_from_gift_card(gift_card_id:,
                                   body:)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `gift_card_id` | `String` | Template, Required | - |
| `body` | [`Unlink Customer From Gift Card Request Hash`](/doc/models/unlink-customer-from-gift-card-request.md) | Body, Required | An object containing the fields to POST for the request.<br><br>See the corresponding object definition for field details. |

## Response Type

[`Unlink Customer From Gift Card Response Hash`](/doc/models/unlink-customer-from-gift-card-response.md)

## Example Usage

```ruby
gift_card_id = 'gift_card_id8'
body = {}
body[:customer_id] = 'GKY0FZ3V717AH8Q2D821PNT2ZW'

result = gift_cards_api.unlink_customer_from_gift_card(gift_card_id: gift_card_id, body: body)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Retrieve Gift Card

Retrieves a gift card using its ID.

```ruby
def retrieve_gift_card(id:)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `String` | Template, Required | The ID of the gift card to retrieve. |

## Response Type

[`Retrieve Gift Card Response Hash`](/doc/models/retrieve-gift-card-response.md)

## Example Usage

```ruby
id = 'id0'

result = gift_cards_api.retrieve_gift_card(id: id)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

