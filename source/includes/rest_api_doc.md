
* * *

## Authenticate

Authenticates a user (logs in a user) and creates a Session which can be used to make subsequent authorized calls. A successful call to AuthenticateUser returns a JSON object containing the user's Id, AccountId, OMSId, and a Session Token.  
Store the Token for session identification on all other requests. Store the UserId, AccountId and OMSId for use in other requests.

#### POST

##### Headers

*   Content-Type: application/json

*   Authorization: Basic Base64Encoded(UserName:Password)  
    Example: Basic dXNlcjpwYXNzd29yZA==

##### Response Payload

<table class="wysiwyg-macro" data-macro-name="code" data-macro-id="42d08a18-531e-4ba2-b560-7e051d830289" data-macro-parameters="language=js" data-macro-schema-version="1" style="background-image: url(https://alphapoint.atlassian.net/wiki/plugins/servlet/confluence/placeholder/macro-heading?definition=e2NvZGU6bGFuZ3VhZ2U9anN9&amp;locale=en_US&amp;version=2); background-repeat: no-repeat;" data-macro-body-type="PLAIN_TEXT">

<tbody>

<tr>

<td class="wysiwyg-macro-body">

<pre>{
	"Authenticated": true,
	"UserId": 1,
	"Token": "9f59e5c1-11cf-4258-b204-0aed329dc96c",
	"AccountId": "4",
	"OMSId": "1"
}</pre>

</td>

</tr>

</tbody>

</table>

<table data-layout="default" class="confluenceTable"><colgroup><col style="width: 226.67px;"><col style="width: 226.67px;"><col style="width: 226.67px;"></colgroup>

<tbody>

<tr>

<th class="confluenceTh">

Field

</th>

<th class="confluenceTh">

Type

</th>

<th class="confluenceTh">

Description

</th>

</tr>

<tr>

<td class="confluenceTd">

Authenticated

</td>

<td class="confluenceTd">

boolean

</td>

<td class="confluenceTd">

True if successfully authenticated

</td>

</tr>

<tr>

<td class="confluenceTd">

UserId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

Your User Id.

</td>

</tr>

<tr>

<td class="confluenceTd">

Token

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

Your current session token. Put this value into the APToken Header on authorized requests.

</td>

</tr>

<tr>

<td class="confluenceTd">

AccountId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

Your Account Id. Use this anywhere an AccountId is a required field.

</td>

</tr>

<tr>

<td class="confluenceTd">

OMSId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The ID of the Order Management System your user belongs to. Use this value anywhere OMSId is a required field.

</td>

</tr>

</tbody>

</table>

## GetProducts

Returns an array of objects for each Product (Asset or Currency) on the exchange.

#### GET

##### URL-Encoded Parameters

*   OMSId [integer] The OMSId you received in the AuthenticateUser Response.

##### Response Payload

<table class="wysiwyg-macro" data-macro-name="code" data-macro-id="19d62fc5-a635-465b-ad44-775654172d8a" data-macro-parameters="language=js" data-macro-schema-version="1" style="background-image: url(https://alphapoint.atlassian.net/wiki/plugins/servlet/confluence/placeholder/macro-heading?definition=e2NvZGU6bGFuZ3VhZ2U9anN9&amp;locale=en_US&amp;version=2); background-repeat: no-repeat;" data-macro-body-type="PLAIN_TEXT">

<tbody>

<tr>

<td class="wysiwyg-macro-body">

<pre>[{
		"OMSId": 1,
		"ProductId": 1,
		"Product": "BTC",
		"ProductFullName": "BTC",
		"ProductType": "CryptoCurrency",
		"DecimalPlaces": 8,
		"TickSize": 0.00000001,
		"NoFees": false
	}, {
		"OMSId": 1,
		"ProductId": 2,
		"Product": "USD",
		"ProductFullName": "USD",
		"ProductType": "NationalCurrency",
		"DecimalPlaces": 2,
		"TickSize": 0.01,
		"NoFees": false
	}
]</pre>

</td>

</tr>

</tbody>

</table>

<table data-layout="default" class="confluenceTable"><colgroup><col style="width: 226.67px;"><col style="width: 226.67px;"><col style="width: 226.67px;"></colgroup>

<tbody>

<tr>

<th class="confluenceTh">

Field

</th>

<th class="confluenceTh">

Type

</th>

<th class="confluenceTh">

Description

</th>

</tr>

<tr>

<td class="confluenceTd">

OMSId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The Order Management System ID.

</td>

</tr>

<tr>

<td class="confluenceTd">

ProductId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

Identifies the product using an integer value.

</td>

</tr>

<tr>

<td class="confluenceTd">

Product

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

Symbol of the product.

</td>

</tr>

<tr>

<td class="confluenceTd">

ProductFullName

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

The long or full name of the product.

</td>

</tr>

<tr>

<td class="confluenceTd">

ProductType

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

NationalCurrency or CryptoCurrency

</td>

</tr>

<tr>

<td class="confluenceTd">

DecimalPlaces

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

Number of decimal places representing the smallest unit of the product.

</td>

</tr>

<tr>

<td class="confluenceTd">

TickSize

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

Same as DecimalPlaces as a real value. Smallest possible real unit of the product.

</td>

</tr>

<tr>

<td class="confluenceTd">

NoFees

</td>

<td class="confluenceTd">

boolean

</td>

<td class="confluenceTd">

Specifies if fees cannot be taken in this product. (In the case where this is true, fees will usually be taken in another product depending on the pair.)

</td>

</tr>

</tbody>

</table>

## GetInstruments

Returns an array of objects for each Instrument (Trade-able pair of assets) on the exchange.

#### GET

##### URL-Encoded Parameters

*   OMSId [Integer]

##### Response Payload

<table class="wysiwyg-macro" data-macro-name="code" data-macro-id="8a772260-4e17-4a08-9b81-1c1a415653c0" data-macro-parameters="language=js" data-macro-schema-version="1" style="background-image: url(https://alphapoint.atlassian.net/wiki/plugins/servlet/confluence/placeholder/macro-heading?definition=e2NvZGU6bGFuZ3VhZ2U9anN9&amp;locale=en_US&amp;version=2); background-repeat: no-repeat;" data-macro-body-type="PLAIN_TEXT">

<tbody>

<tr>

<td class="wysiwyg-macro-body">

<pre>[{
		"OMSId": 1,
		"InstrumentId": 1,
		"Symbol": "BTCUSD",
		"Product1": 1,
		"Product1Symbol": "BTC",
		"Product2": 2,
		"Product2Symbol": "USD",
		"InstrumentType": "Standard",
		"VenueInstrumentId": 1,
		"VenueId": 1,
		"SortIndex": 0,
		"SessionStatus": "Unknown",
		"PreviousSessionStatus": "Unknown",
		"SessionStatusDateTime": "0001-01-01T05:00:00Z",
		"SelfTradePrevention": false,
		"QuantityIncrement": 0.00000001
	}, {
		"OMSId": 1,
		"InstrumentId": 2,
		"Symbol": "A0USD",
		"Product1": 3,
		"Product1Symbol": "PE0",
		"Product2": 2,
		"Product2Symbol": "USD",
		"InstrumentType": "Standard",
		"VenueInstrumentId": 2,
		"VenueId": 1,
		"SortIndex": 0,
		"SessionStatus": "Unknown",
		"PreviousSessionStatus": "Unknown",
		"SessionStatusDateTime": "0001-01-01T05:00:00Z",
		"SelfTradePrevention": false,
		"QuantityIncrement": 0.01
	}
]</pre>

</td>

</tr>

</tbody>

</table>

<table data-layout="default" class="confluenceTable"><colgroup><col style="width: 226.67px;"><col style="width: 226.67px;"><col style="width: 226.67px;"></colgroup>

<tbody>

<tr>

<th class="confluenceTh">

Field

</th>

<th class="confluenceTh">

Type

</th>

<th class="confluenceTh">

Description

</th>

</tr>

<tr>

<td class="confluenceTd">

OMSId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The Order Management System ID.

</td>

</tr>

<tr>

<td class="confluenceTd">

InstrumentId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The numeric ID of the Instrument

</td>

</tr>

<tr>

<td class="confluenceTd">

Symbol

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

The string ID of the Instrument

</td>

</tr>

<tr>

<td class="confluenceTd">

Product1

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The numeric ProductId of the first Product which makes up the pair.

</td>

</tr>

<tr>

<td class="confluenceTd">

Product1Symbol

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

The string identifier of the first Product which makes up the pair.

</td>

</tr>

<tr>

<td class="confluenceTd">

Product2

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The numeric ProductId of the second Product which makes up the pair.

</td>

</tr>

<tr>

<td class="confluenceTd">

Product2Symbol

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

The string identifier of the second Product which makes up the pair.

</td>

</tr>

<tr>

<td class="confluenceTd">

InstrumentType

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

Describes the type of instrument this is. Usually "Standard"

</td>

</tr>

<tr>

<td class="confluenceTd">

VenueInstrumentId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

Describes the ID of the instrument on the matching engine.

</td>

</tr>

<tr>

<td class="confluenceTd">

VenueId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

Describes the ID of the matching engine the Instrument resides on.

</td>

</tr>

<tr>

<td class="confluenceTd">

SortIndex

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

Sometimes used to sort Instruments visibly on a UI.

</td>

</tr>

<tr>

<td class="confluenceTd">

SessionStatus

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

Describes the market state for this instrument. "Running", "Paused", "Halted"

</td>

</tr>

<tr>

<td class="confluenceTd">

PreviousSessionStatus

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

Describes the previous market state for this instrument. "Running", "Paused", "Halted"

</td>

</tr>

<tr>

<td class="confluenceTd">

SessionStatusDateTime

</td>

<td class="confluenceTd">

string/datetime

</td>

<td class="confluenceTd">

The time the current SessionStatus went into effect.

</td>

</tr>

<tr>

<td class="confluenceTd">

QuantityIncrement

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The smallest tradeable quantity for this Instrument.

</td>

</tr>

</tbody>

</table>

## GetAccountPositions

Retrieves a list of positions (balances) and related information.

#### GET

##### Headers

*   APToken [Token string supplied in AuthenticateUser Response]

##### URL-Encoded Parameters

*   OMSId [Integer]

*   AccountId [Integer]

##### Response Payload

<table class="wysiwyg-macro" data-macro-name="code" data-macro-id="fcd3f6e4-3664-4615-be9b-63280dddc202" data-macro-parameters="language=js" data-macro-schema-version="1" data-macro-body-type="PLAIN_TEXT">

<tbody>

<tr>

<td class="wysiwyg-macro-body">

<pre>[{
		"OMSId": 1,
		"AccountId": 4,
		"ProductSymbol": "BTC",
		"ProductId": 1,
		"Amount": 0,
		"Hold": 0,
		"PendingDeposits": 0,
		"PendingWithdraws": 0,
		"TotalDayDeposits": 0,
		"TotalDayWithdraws": 0,
		"TotalMonthWithdraws": 0
	}, {
		"OMSId": 1,
		"AccountId": 4,
		"ProductSymbol": "USD",
		"ProductId": 2,
		"Amount": 0,
		"Hold": 0,
		"PendingDeposits": 0,
		"PendingWithdraws": 0,
		"TotalDayDeposits": 0,
		"TotalDayWithdraws": 0,
		"TotalMonthWithdraws": 0
	}
]</pre>

</td>

</tr>

</tbody>

</table>

<table data-layout="default" class="confluenceTable"><colgroup><col style="width: 226.67px;"><col style="width: 226.67px;"><col style="width: 226.67px;"></colgroup>

<tbody>

<tr>

<th class="confluenceTh">

Field

</th>

<th class="confluenceTh">

Type

</th>

<th class="confluenceTh">

Description

</th>

</tr>

<tr>

<td class="confluenceTd">

OMSId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The Order Management System ID.

</td>

</tr>

<tr>

<td class="confluenceTd">

AccountId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The Account the position/balance is for.

</td>

</tr>

<tr>

<td class="confluenceTd">

ProductSymbol

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

The symbol of the product the position/balance is for.

</td>

</tr>

<tr>

<td class="confluenceTd">

ProductId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The ID of the product the position/balance is for.

</td>

</tr>

<tr>

<td class="confluenceTd">

Amount

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The total balance/position, including any amount held.

</td>

</tr>

<tr>

<td class="confluenceTd">

Hold

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

Represents the amount of the balance that is on hold and cannot be traded or withdrawn.

</td>

</tr>

<tr>

<td class="confluenceTd">

PendingDeposits

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

Total amount of deposits not yet confirmed.

</td>

</tr>

<tr>

<td class="confluenceTd">

PendingWithdraws

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

Total amount of withdraws not yet confirmed.

</td>

</tr>

<tr>

<td class="confluenceTd">

TotalDayDeposits

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

Total amount of deposits in the last 24 hours.

</td>

</tr>

<tr>

<td class="confluenceTd">

TotalDayWithdraws

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

Total amount of withdraws in the last 24 hours.

</td>

</tr>

<tr>

<td class="confluenceTd">

TotalMonthWithdraws

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

Total amount of withdraws in the last 30 days.

</td>

</tr>

</tbody>

</table>

## GetOpenOrders

Returns an array of 0 or more orders that are still active on the market. The call returns an empty array if a user has no open orders.

#### GET

##### Headers

*   APToken [Token string supplied in AuthenticateUser Response]

##### URL-Encoded Parameters

*   OMSId [Integer]

*   AccountId [Integer]

##### Response Payload

<table class="wysiwyg-macro" data-macro-name="code" data-macro-id="f1bcb8e7-5f1f-479b-a9c1-349a0197ea23" data-macro-parameters="language=js" data-macro-schema-version="1"  data-macro-body-type="PLAIN_TEXT">

<tbody>

<tr>

<td class="wysiwyg-macro-body">

<pre>[{
		"Side": "Buy",
		"OrderId": 15069,
		"Price": 95,
		"Quantity": 1,
		"DisplayQuantity": 1,
		"Instrument": 1,
		"Account": 4,
		"OrderType": "Limit",
		"ClientOrderId": 99,
		"OrderState": "Working",
		"ReceiveTime": 1503077068361,
		"ReceiveTimeTicks": 636386738683614156,
		"OrigQuantity": 1,
		"QuantityExecuted": 0,
		"AvgPrice": 0,
		"CounterPartyId": 0,
		"ChangeReason": "NewInputAccepted",
		"OrigOrderId": 15069,
		"OrigClOrdId": 99,
		"EnteredBy": 1,
		"IsQuote": false,
		"InsideAsk": 9223372036.854775807,
		"InsideAskSize": 0,
		"InsideBid": 95,
		"InsideBidSize": 6.82,
		"LastTradePrice": 1,
		"RejectReason": "",
		"IsLockedIn": false,
		"CancelReason": null,
		"OMSId": 1
	}
]</pre>

</td>

</tr>

</tbody>

</table>

<table data-layout="default" class="confluenceTable"><colgroup><col style="width: 226.67px;"><col style="width: 226.67px;"><col style="width: 226.67px;"></colgroup>

<tbody>

<tr>

<th class="confluenceTh">

Field

</th>

<th class="confluenceTh">

Type

</th>

<th class="confluenceTh">

Description

</th>

</tr>

<tr>

<td class="confluenceTd">

Side

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

"Buy" or "Sell"

</td>

</tr>

<tr>

<td class="confluenceTd">

OrderId

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

The server Id of the order.

</td>

</tr>

<tr>

<td class="confluenceTd">

Price

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

Price of the Order.

</td>

</tr>

<tr>

<td class="confluenceTd">

Quantity

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

Quantity remaining on the order.

</td>

</tr>

<tr>

<td class="confluenceTd">

DisplayQuantity

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The maximum amount of quantity shown in public market data. Usually equal to the Quantity.

</td>

</tr>

<tr>

<td class="confluenceTd">

Instrument

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The InstrumentId the order is for.

</td>

</tr>

<tr>

<td class="confluenceTd">

Account

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The Account the order belongs to.

</td>

</tr>

<tr>

<td class="confluenceTd">

OrderType

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

"Market", "Limit", "StopMarket", "StopLimit", "TrailingStopMarket", "TrailingStopLimit", "BlockTrade"

</td>

</tr>

<tr>

<td class="confluenceTd">

ClientOrderId

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

User submitted Id of the order.

</td>

</tr>

<tr>

<td class="confluenceTd">

OrderState

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

"Working", "FullyExecuted", "Expired", "Canceled", "Rejected"

</td>

</tr>

<tr>

<td class="confluenceTd">

ReceiveTime

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

UTC Epoch Time the order was received.

</td>

</tr>

<tr>

<td class="confluenceTd">

ReceiveTimeTicks

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

Microsoft Ticks Time the order was received.

</td>

</tr>

<tr>

<td class="confluenceTd">

OrigQuantity

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The original quantity the order was submitted for.

</td>

</tr>

<tr>

<td class="confluenceTd">

QuantityExecuted

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The total amount executed against this order.

</td>

</tr>

<tr>

<td class="confluenceTd">

AvgPrice

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

DEPRECATED

</td>

</tr>

<tr>

<td class="confluenceTd">

CounterPartyId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

This will be 0 unless this is a BlockTrade, in which case it represents the Id of the counterparty the BlockTrade is submitted for.

</td>

</tr>

<tr>

<td class="confluenceTd">

ChangeReason

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

"NewInputAccepted", "NewInputRejected", "OtherRejected", "Expired", "Trade", "SystemCanceled_NoMoreMarket", "SystemCanceled_BelowMinimum", "SystemCanceled_PriceCollar", "SystemCanceled_MarginFailed"

</td>

</tr>

<tr>

<td class="confluenceTd">

OrigOrderId

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

If this is a replacement order in a CancelReplaceOrder instruction, this is the OrderId of the canceled order.

</td>

</tr>

<tr>

<td class="confluenceTd">

OrigClOrdId

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

If this is a replacement order in a CancelReplaceOrder instruction, this is the Client Order Id of the canceled order.

</td>

</tr>

<tr>

<td class="confluenceTd">

EnteredBy

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The UserId of the user who entered this order.

</td>

</tr>

<tr>

<td class="confluenceTd">

IsQuote

</td>

<td class="confluenceTd">

boolean

</td>

<td class="confluenceTd">

Specifies if this is a Market Maker Quote.

</td>

</tr>

<tr>

<td class="confluenceTd">

InsideAsk

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The inside (best) ask at the time this order state was last updated.

</td>

</tr>

<tr>

<td class="confluenceTd">

InsideAskSize

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The quantity of the inside (best) ask at the time this order state was last updated.

</td>

</tr>

<tr>

<td class="confluenceTd">

InsideBid

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The inside (best) bid at the time this order state was last updated.

</td>

</tr>

<tr>

<td class="confluenceTd">

InsideBidSize

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The quantity of the inside (best) bid at the time this order state was last updated.

</td>

</tr>

<tr>

<td class="confluenceTd">

LastTradePrice

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The price of the last trade at the time this order state was last updated.

</td>

</tr>

<tr>

<td class="confluenceTd">

RejectReason

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

A description of the reason for rejection, if the OrderState is "Rejected".

</td>

</tr>

<tr>

<td class="confluenceTd">

IsLockedIn

</td>

<td class="confluenceTd">

boolean

</td>

<td class="confluenceTd">

In the event the order is a BlockTrade, this describes if only one party is required to enter the trade.

</td>

</tr>

<tr>

<td class="confluenceTd">

CancelReason

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

Describes any comment or reason for an Admin cancellation of this order.

</td>

</tr>

<tr>

<td class="confluenceTd">

OMSId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The Order Management System ID.

</td>

</tr>

</tbody>

</table>

## GetOrderHistory

Returns a complete list of all orders, open, filled, canceled and rejected. Limited to 100.

##### Headers

*   APToken [Token string supplied in AuthenticateUser Response]

##### URL-Encoded Parameters

*   OMSId [Integer]

*   AccountId [Integer]

##### Response Payload

<table class="wysiwyg-macro" data-macro-name="code" data-macro-id="c3e6fd79-28d9-42ed-b16a-1cfae75b4560" data-macro-parameters="language=js" data-macro-schema-version="1" style="background-image: url(https://alphapoint.atlassian.net/wiki/plugins/servlet/confluence/placeholder/macro-heading?definition=e2NvZGU6bGFuZ3VhZ2U9anN9&amp;locale=en_US&amp;version=2); background-repeat: no-repeat;" data-macro-body-type="PLAIN_TEXT">

<tbody>

<tr>

<td class="wysiwyg-macro-body">

<pre>[{
		"Side": "Buy",
		"OrderId": 15069,
		"Price": 95,
		"Quantity": 1,
		"DisplayQuantity": 1,
		"Instrument": 1,
		"Account": 4,
		"OrderType": "Limit",
		"ClientOrderId": 99,
		"OrderState": "Working",
		"ReceiveTime": 1503077068361,
		"ReceiveTimeTicks": 636386738683614156,
		"OrigQuantity": 1,
		"QuantityExecuted": 0,
		"AvgPrice": 0,
		"CounterPartyId": 0,
		"ChangeReason": "NewInputAccepted",
		"OrigOrderId": 15069,
		"OrigClOrdId": 99,
		"EnteredBy": 1,
		"IsQuote": false,
		"InsideAsk": 9223372036.854775807,
		"InsideAskSize": 0,
		"InsideBid": 95,
		"InsideBidSize": 6.82,
		"LastTradePrice": 1,
		"RejectReason": "",
		"IsLockedIn": false,
		"CancelReason": null,
		"OMSId": 1
	}, {
		"Side": "Buy",
		"OrderId": 15068,
		"Price": 95,
		"Quantity": 0,
		"DisplayQuantity": 1,
		"Instrument": 1,
		"Account": 4,
		"OrderType": "Limit",
		"ClientOrderId": 15067,
		"OrderState": "Canceled",
		"ReceiveTime": 1503076964272,
		"ReceiveTimeTicks": 636386737642718166,
		"OrigQuantity": 1,
		"QuantityExecuted": 0,
		"AvgPrice": 0,
		"CounterPartyId": 0,
		"ChangeReason": "UserModified",
		"OrigOrderId": 15067,
		"OrigClOrdId": 99,
		"EnteredBy": 1,
		"IsQuote": false,
		"InsideAsk": 9223372036.854775807,
		"InsideAskSize": 0,
		"InsideBid": 95,
		"InsideBidSize": 6.82,
		"LastTradePrice": 1,
		"RejectReason": "",
		"IsLockedIn": false,
		"CancelReason": "UserModified",
		"OMSId": 1
	}
]</pre>

</td>

</tr>

</tbody>

</table>

<table data-layout="default" class="confluenceTable"><colgroup><col style="width: 226.67px;"><col style="width: 226.67px;"><col style="width: 226.67px;"></colgroup>

<tbody>

<tr>

<th class="confluenceTh">

Field

</th>

<th class="confluenceTh">

Type

</th>

<th class="confluenceTh">

Description

</th>

</tr>

<tr>

<td class="confluenceTd">

Side

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

"Buy" or "Sell"

</td>

</tr>

<tr>

<td class="confluenceTd">

OrderId

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

The server Id of the order.

</td>

</tr>

<tr>

<td class="confluenceTd">

Price

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

Price of the Order.

</td>

</tr>

<tr>

<td class="confluenceTd">

Quantity

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

Quantity remaining on the order.

</td>

</tr>

<tr>

<td class="confluenceTd">

DisplayQuantity

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The maximum amount of quantity shown in public market data. Usually equal to the Quantity.

</td>

</tr>

<tr>

<td class="confluenceTd">

Instrument

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The InstrumentId the order is for.

</td>

</tr>

<tr>

<td class="confluenceTd">

Account

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The Account the order belongs to.

</td>

</tr>

<tr>

<td class="confluenceTd">

OrderType

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

"Market", "Limit", "StopMarket", "StopLimit", "TrailingStopMarket", "TrailingStopLimit", "BlockTrade"

</td>

</tr>

<tr>

<td class="confluenceTd">

ClientOrderId

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

User submitted Id of the order.

</td>

</tr>

<tr>

<td class="confluenceTd">

OrderState

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

"Working", "FullyExecuted", "Expired", "Canceled", "Rejected"

</td>

</tr>

<tr>

<td class="confluenceTd">

ReceiveTime

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

UTC Epoch Time the order was received.

</td>

</tr>

<tr>

<td class="confluenceTd">

ReceiveTimeTicks

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

Microsoft Ticks Time the order was received.

</td>

</tr>

<tr>

<td class="confluenceTd">

OrigQuantity

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The original quantity the order was submitted for.

</td>

</tr>

<tr>

<td class="confluenceTd">

QuantityExecuted

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The total amount executed against this order.

</td>

</tr>

<tr>

<td class="confluenceTd">

AvgPrice

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

DEPRECATED

</td>

</tr>

<tr>

<td class="confluenceTd">

CounterPartyId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

This will be 0 unless this is a BlockTrade, in which case it represents the Id of the counterparty the BlockTrade is submitted for.

</td>

</tr>

<tr>

<td class="confluenceTd">

ChangeReason

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

"NewInputAccepted", "NewInputRejected", "OtherRejected", "Expired", "Trade", "SystemCanceled_NoMoreMarket", "SystemCanceled_BelowMinimum", "SystemCanceled_PriceCollar", "SystemCanceled_MarginFailed"

</td>

</tr>

<tr>

<td class="confluenceTd">

OrigOrderId

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

If this is a replacement order in a CancelReplaceOrder instruction, this is the OrderId of the canceled order.

</td>

</tr>

<tr>

<td class="confluenceTd">

OrigClOrdId

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

If this is a replacement order in a CancelReplaceOrder instruction, this is the Client Order Id of the canceled order.

</td>

</tr>

<tr>

<td class="confluenceTd">

EnteredBy

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The UserId of the user who entered this order.

</td>

</tr>

<tr>

<td class="confluenceTd">

IsQuote

</td>

<td class="confluenceTd">

boolean

</td>

<td class="confluenceTd">

Specifies if this is a Market Maker Quote.

</td>

</tr>

<tr>

<td class="confluenceTd">

InsideAsk

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The inside (best) ask at the time this order state was last updated.

</td>

</tr>

<tr>

<td class="confluenceTd">

InsideAskSize

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The quantity of the inside (best) ask at the time this order state was last updated.

</td>

</tr>

<tr>

<td class="confluenceTd">

InsideBid

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The inside (best) bid at the time this order state was last updated.

</td>

</tr>

<tr>

<td class="confluenceTd">

InsideBidSize

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The quantity of the inside (best) bid at the time this order state was last updated.

</td>

</tr>

<tr>

<td class="confluenceTd">

LastTradePrice

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The price of the last trade at the time this order state was last updated.

</td>

</tr>

<tr>

<td class="confluenceTd">

RejectReason

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

A description of the reason for rejection, if the OrderState is "Rejected".

</td>

</tr>

<tr>

<td class="confluenceTd">

IsLockedIn

</td>

<td class="confluenceTd">

boolean

</td>

<td class="confluenceTd">

In the event the order is a BlockTrade, this describes if only one party is required to enter the trade.

</td>

</tr>

<tr>

<td class="confluenceTd">

CancelReason

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

Describes any comment or reason for an Admin cancellation of this order.

</td>

</tr>

<tr>

<td class="confluenceTd">

OMSId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The Order Management System ID.

</td>

</tr>

</tbody>

</table>

## GetOrderStatus

Retrieves the status of a single order.

#### GET

##### Headers

*   APToken [Token string supplied in AuthenticateUser Response]

##### URL-Encoded Parameters

*   OMSId [Integer]

*   AccountId [Integer]

*   OrderId [Long]

##### Response Payload

<table class="wysiwyg-macro" data-macro-name="code" data-macro-id="0a3b4133-c471-4552-ada3-7abe4b7e0325" data-macro-parameters="language=js" data-macro-schema-version="1" style="background-image: url(https://alphapoint.atlassian.net/wiki/plugins/servlet/confluence/placeholder/macro-heading?definition=e2NvZGU6bGFuZ3VhZ2U9anN9&amp;locale=en_US&amp;version=2); background-repeat: no-repeat;" data-macro-body-type="PLAIN_TEXT">

<tbody>

<tr>

<td class="wysiwyg-macro-body">

<pre>{
	"Side": "Buy",
	"OrderId": 15069,
	"Price": 95,
	"Quantity": 1,
	"DisplayQuantity": 1,
	"Instrument": 1,
	"Account": 4,
	"OrderType": "Limit",
	"ClientOrderId": 99,
	"OrderState": "Working",
	"ReceiveTime": 1503077068361,
	"ReceiveTimeTicks": 636386738683614156,
	"OrigQuantity": 1,
	"QuantityExecuted": 0,
	"AvgPrice": 0,
	"CounterPartyId": 0,
	"ChangeReason": "NewInputAccepted",
	"OrigOrderId": 15069,
	"OrigClOrdId": 99,
	"EnteredBy": 1,
	"IsQuote": false,
	"InsideAsk": 9223372036.854775807,
	"InsideAskSize": 0,
	"InsideBid": 95,
	"InsideBidSize": 6.82,
	"LastTradePrice": 1,
	"RejectReason": "",
	"IsLockedIn": false,
	"CancelReason": null,
	"OMSId": 1
}</pre>

</td>

</tr>

</tbody>

</table>

<table data-layout="default" class="confluenceTable"><colgroup><col style="width: 226.67px;"><col style="width: 226.67px;"><col style="width: 226.67px;"></colgroup>

<tbody>

<tr>

<th class="confluenceTh">

Field

</th>

<th class="confluenceTh">

Type

</th>

<th class="confluenceTh">

Description

</th>

</tr>

<tr>

<td class="confluenceTd">

Side

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

"Buy" or "Sell"

</td>

</tr>

<tr>

<td class="confluenceTd">

OrderId

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

The server Id of the order.

</td>

</tr>

<tr>

<td class="confluenceTd">

Price

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

Price of the Order.

</td>

</tr>

<tr>

<td class="confluenceTd">

Quantity

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

Quantity remaining on the order.

</td>

</tr>

<tr>

<td class="confluenceTd">

DisplayQuantity

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The maximum amount of quantity shown in public market data. Usually equal to the Quantity.

</td>

</tr>

<tr>

<td class="confluenceTd">

Instrument

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The InstrumentId the order is for.

</td>

</tr>

<tr>

<td class="confluenceTd">

Account

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The Account the order belongs to.

</td>

</tr>

<tr>

<td class="confluenceTd">

OrderType

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

"Market", "Limit", "StopMarket", "StopLimit", "TrailingStopMarket", "TrailingStopLimit", "BlockTrade"

</td>

</tr>

<tr>

<td class="confluenceTd">

ClientOrderId

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

User submitted Id of the order.

</td>

</tr>

<tr>

<td class="confluenceTd">

OrderState

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

"Working", "FullyExecuted", "Expired", "Canceled", "Rejected"

</td>

</tr>

<tr>

<td class="confluenceTd">

ReceiveTime

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

UTC Epoch Time the order was received.

</td>

</tr>

<tr>

<td class="confluenceTd">

ReceiveTimeTicks

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

Microsoft Ticks Time the order was received.

</td>

</tr>

<tr>

<td class="confluenceTd">

OrigQuantity

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The original quantity the order was submitted for.

</td>

</tr>

<tr>

<td class="confluenceTd">

QuantityExecuted

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The total amount executed against this order.

</td>

</tr>

<tr>

<td class="confluenceTd">

AvgPrice

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

DEPRECATED

</td>

</tr>

<tr>

<td class="confluenceTd">

CounterPartyId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

This will be 0 unless this is a BlockTrade, in which case it represents the Id of the counterparty the BlockTrade is submitted for.

</td>

</tr>

<tr>

<td class="confluenceTd">

ChangeReason

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

"NewInputAccepted", "NewInputRejected", "OtherRejected", "Expired", "Trade", "SystemCanceled_NoMoreMarket", "SystemCanceled_BelowMinimum", "SystemCanceled_PriceCollar", "SystemCanceled_MarginFailed"

</td>

</tr>

<tr>

<td class="confluenceTd">

OrigOrderId

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

If this is a replacement order in a CancelReplaceOrder instruction, this is the OrderId of the canceled order.

</td>

</tr>

<tr>

<td class="confluenceTd">

OrigClOrdId

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

If this is a replacement order in a CancelReplaceOrder instruction, this is the Client Order Id of the canceled order.

</td>

</tr>

<tr>

<td class="confluenceTd">

EnteredBy

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The UserId of the user who entered this order.

</td>

</tr>

<tr>

<td class="confluenceTd">

IsQuote

</td>

<td class="confluenceTd">

boolean

</td>

<td class="confluenceTd">

Specifies if this is a Market Maker Quote.

</td>

</tr>

<tr>

<td class="confluenceTd">

InsideAsk

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The inside (best) ask at the time this order state was last updated.

</td>

</tr>

<tr>

<td class="confluenceTd">

InsideAskSize

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The quantity of the inside (best) ask at the time this order state was last updated.

</td>

</tr>

<tr>

<td class="confluenceTd">

InsideBid

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The inside (best) bid at the time this order state was last updated.

</td>

</tr>

<tr>

<td class="confluenceTd">

InsideBidSize

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The quantity of the inside (best) bid at the time this order state was last updated.

</td>

</tr>

<tr>

<td class="confluenceTd">

LastTradePrice

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The price of the last trade at the time this order state was last updated.

</td>

</tr>

<tr>

<td class="confluenceTd">

RejectReason

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

A description of the reason for rejection, if the OrderState is "Rejected".

</td>

</tr>

<tr>

<td class="confluenceTd">

IsLockedIn

</td>

<td class="confluenceTd">

boolean

</td>

<td class="confluenceTd">

In the event the order is a BlockTrade, this describes if only one party is required to enter the trade.

</td>

</tr>

<tr>

<td class="confluenceTd">

CancelReason

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

Describes any comment or reason for an Admin cancellation of this order.

</td>

</tr>

<tr>

<td class="confluenceTd">

OMSId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The Order Management System ID.

</td>

</tr>

</tbody>

</table>

## SendOrder

#### POST

##### Headers

*   Content-Type=application/json

*   APToken=[Token string supplied in AuthenticateUser Response]

##### Body

<table class="wysiwyg-macro" data-macro-name="code" data-macro-id="ef912359-d8e5-4091-a432-ff77c28af88e" data-macro-parameters="language=js" data-macro-schema-version="1" style="background-image: url(https://alphapoint.atlassian.net/wiki/plugins/servlet/confluence/placeholder/macro-heading?definition=e2NvZGU6bGFuZ3VhZ2U9anN9&amp;locale=en_US&amp;version=2); background-repeat: no-repeat;" data-macro-body-type="PLAIN_TEXT">

<tbody>

<tr>

<td class="wysiwyg-macro-body">

<pre>{
    "AccountId": 5,
    "ClientOrderId": 99,
    "Quantity": 1,
    "DisplayQuantity": 0,
    "LimitPrice": 95,
    "OrderIdOCO": 0, 
    "OrderType": "Limit", 
    "PegPriceType": "Midpoint",
    "InstrumentId": 1,
    "TrailingAmount": 1.0,
    "LimitOffset": 2.0, 
    "Side": 0, 
    "StopPrice": 96,
    "TimeInForce": 1,
    "OMSId": 1 
}</pre>

</td>

</tr>

</tbody>

</table>

<table data-layout="default" class="confluenceTable"><colgroup><col style="width: 170.0px;"><col style="width: 170.0px;"><col style="width: 170.0px;"><col style="width: 170.0px;"></colgroup>

<tbody>

<tr>

<th class="confluenceTh">

Field

</th>

<th class="confluenceTh">

Type

</th>

<th class="confluenceTh">

Description

</th>

<th class="confluenceTh">

Required

</th>

</tr>

<tr>

<td class="confluenceTd">

AccountId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The AccountId to submit this order on.

</td>

<td class="confluenceTd">

Y

</td>

</tr>

<tr>

<td class="confluenceTd">

ClientOrderId

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

A client supplied Identifier for the order.

</td>

<td class="confluenceTd">

N

</td>

</tr>

<tr>

<td class="confluenceTd">

Quantity

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The amount/quantity to submit the order for.

</td>

<td class="confluenceTd">

Y

</td>

</tr>

<tr>

<td class="confluenceTd">

DisplayQuantity

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

Specifies the maximum amount to display on the book at any one time.

</td>

<td class="confluenceTd">

N

</td>

</tr>

<tr>

<td class="confluenceTd">

LimitPrice

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The price the order is for. Optional for Market Orders.

</td>

<td class="confluenceTd">

N

</td>

</tr>

<tr>

<td class="confluenceTd">

OrderIdOCO

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

Not Used.

</td>

<td class="confluenceTd">

N

</td>

</tr>

<tr>

<td class="confluenceTd">

OrderType

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

"Market", "Limit", "StopMarket", "StopLimit", "TrailingStopMarket", "TrailingStopLimit", "BlockTrade"

</td>

<td class="confluenceTd">

Y

</td>

</tr>

<tr>

<td class="confluenceTd">

PegPriceType

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

Describes how a trailing price is calculated. Options: "Last", "Bid", "Ask", "Midpoint"

</td>

<td class="confluenceTd">

N

</td>

</tr>

<tr>

<td class="confluenceTd">

InstrumentId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

Specifies the Instrument this order is for.

</td>

<td class="confluenceTd">

Y

</td>

</tr>

<tr>

<td class="confluenceTd">

TrailingAmount

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The distance from the market price to trail by, used only for Trailing orders.

</td>

<td class="confluenceTd">

N

</td>

</tr>

<tr>

<td class="confluenceTd">

LimitOffset

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The offset to place a Limit order at when the trailing price is crossed. Used only in TrailingStopLimit orders.

</td>

<td class="confluenceTd">

N

</td>

</tr>

<tr>

<td class="confluenceTd">

Side

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

"Buy" or "Sell"

</td>

<td class="confluenceTd">

Y

</td>

</tr>

<tr>

<td class="confluenceTd">

StopPrice

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The price a Stop order is to be placed at once triggered.

</td>

<td class="confluenceTd">

N

</td>

</tr>

<tr>

<td class="confluenceTd">

TimeInForce

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

"GTC", "IOC", "FOK"

</td>

<td class="confluenceTd">

Y

</td>

</tr>

<tr>

<td class="confluenceTd">

OMSId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The Order Management System the Account and Instrument reside on. Generally the same as the OMSId returned by AuthenticateUser.

</td>

<td class="confluenceTd">

Y

</td>

</tr>

</tbody>

</table>

##### Response Payload

<table class="wysiwyg-macro" data-macro-name="code" data-macro-id="60d50baf-d0b8-4398-831e-e4581efecec8" data-macro-parameters="language=js" data-macro-schema-version="1" style="background-image: url(https://alphapoint.atlassian.net/wiki/plugins/servlet/confluence/placeholder/macro-heading?definition=e2NvZGU6bGFuZ3VhZ2U9anN9&amp;locale=en_US&amp;version=2); background-repeat: no-repeat;" data-macro-body-type="PLAIN_TEXT">

<tbody>

<tr>

<td class="wysiwyg-macro-body">

<pre>{
	"status": "Accepted",
	"errormsg": "",
	"OrderId": 15047
}</pre>

</td>

</tr>

</tbody>

</table>

## ModifyOrder

#### POST

##### Headers

*   Content-Type=application/json

*   APToken=[Token string supplied in AuthenticateUser Response]

##### Body

<table class="wysiwyg-macro" data-macro-name="code" data-macro-id="8f95991f-9fe3-41aa-88af-1898b109fcc5" data-macro-parameters="language=js" data-macro-schema-version="1" style="background-image: url(https://alphapoint.atlassian.net/wiki/plugins/servlet/confluence/placeholder/macro-heading?definition=e2NvZGU6bGFuZ3VhZ2U9anN9&amp;locale=en_US&amp;version=2); background-repeat: no-repeat;" data-macro-body-type="PLAIN_TEXT">

<tbody>

<tr>

<td class="wysiwyg-macro-body">

<pre>{ 
    "OMSId":1, 
    "OrderId": 15049,
    "InstrumentId":1, 
    "PreviousOrderRevision":0, 
    "Quantity":0.9
}</pre>

</td>

</tr>

</tbody>

</table>

<table data-layout="default" class="confluenceTable"><colgroup><col style="width: 170.0px;"><col style="width: 170.0px;"><col style="width: 170.0px;"><col style="width: 170.0px;"></colgroup>

<tbody>

<tr>

<th class="confluenceTh">

Field

</th>

<th class="confluenceTh">

Type

</th>

<th class="confluenceTh">

Description

</th>

<th class="confluenceTh">

Required

</th>

</tr>

<tr>

<td class="confluenceTd">

OMSId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The Order Management System the Account and Instrument reside on. Generally the same as the OMSId returned by AuthenticateUser.

</td>

<td class="confluenceTd">

Y

</td>

</tr>

<tr>

<td class="confluenceTd">

OrderId

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

The Server Order Id of the Order to modify.

</td>

<td class="confluenceTd">

Y

</td>

</tr>

<tr>

<td class="confluenceTd">

InstrumentId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The Instrument the order is for.

</td>

<td class="confluenceTd">

Y

</td>

</tr>

<tr>

<td class="confluenceTd">

PreviousOrderRevision

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

Safe to leave as 0.

</td>

<td class="confluenceTd">

N

</td>

</tr>

<tr>

<td class="confluenceTd">

Quantity

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The new Quantity (must be lower than the current quantity).

</td>

<td class="confluenceTd">

Y

</td>

</tr>

</tbody>

</table>

##### Response Payload

<table class="wysiwyg-macro" data-macro-name="code" data-macro-id="85e89be2-60d8-4f8c-9a5e-4152e08cb604" data-macro-parameters="language=js" data-macro-schema-version="1" style="background-image: url(https://alphapoint.atlassian.net/wiki/plugins/servlet/confluence/placeholder/macro-heading?definition=e2NvZGU6bGFuZ3VhZ2U9anN9&amp;locale=en_US&amp;version=2); background-repeat: no-repeat;" data-macro-body-type="PLAIN_TEXT">

<tbody>

<tr>

<td class="wysiwyg-macro-body">

<pre>{
	"result": true,
	"errormsg": null,
	"errorcode": 0,
	"detail": null
}</pre>

</td>

</tr>

</tbody>

</table>

## CancelReplaceOrder

#### POST

##### Headers

*   Content-Type=application/json

*   APToken=[Token string supplied in AuthenticateUser Response]

##### Body

<table class="wysiwyg-macro" data-macro-name="code" data-macro-id="693d6147-be85-4f37-8dd6-2004280e3f35" data-macro-parameters="language=js" data-macro-schema-version="1" style="background-image: url(https://alphapoint.atlassian.net/wiki/plugins/servlet/confluence/placeholder/macro-heading?definition=e2NvZGU6bGFuZ3VhZ2U9anN9&amp;locale=en_US&amp;version=2); background-repeat: no-repeat;" data-macro-body-type="PLAIN_TEXT">

<tbody>

<tr>

<td class="wysiwyg-macro-body">

<pre>{
    "AccountId": 4,
  	"OrderIdToReplace": 15067,
    "ClientOrderId": 99,
    "Quantity": 1,
    "DisplayQuantity": 0,
    "LimitPrice": 95,
    "OrderIdOCO": 0, 
    "OrderType": 2, 
    "PegPriceType": 1,
    "InstrumentId": 1,
    "TrailingAmount": 1.0,
    "LimitOffset": 2.0, 
    "Side": 0, 
    "StopPrice": 96,
    "TimeInForce": 1,
    "OMSId": 1 
}</pre>

</td>

</tr>

</tbody>

</table>

<table data-layout="default" class="confluenceTable"><colgroup><col style="width: 170.0px;"><col style="width: 170.0px;"><col style="width: 170.0px;"><col style="width: 170.0px;"></colgroup>

<tbody>

<tr>

<th class="confluenceTh">

Field

</th>

<th class="confluenceTh">

Type

</th>

<th class="confluenceTh">

Description

</th>

<th class="confluenceTh">

Required

</th>

</tr>

<tr>

<td class="confluenceTd">

AccountId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The AccountId to submit this order on.

</td>

<td class="confluenceTd">

Y

</td>

</tr>

<tr>

<td class="confluenceTd">

OrderIdToReplace

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

The Server Order Id of the order being replaced.

</td>

<td class="confluenceTd">

Y

</td>

</tr>

<tr>

<td class="confluenceTd">

ClientOrderId

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

A client supplied Identifier for the order.

</td>

<td class="confluenceTd">

N

</td>

</tr>

<tr>

<td class="confluenceTd">

Quantity

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The amount/quantity to submit the order for.

</td>

<td class="confluenceTd">

Y

</td>

</tr>

<tr>

<td class="confluenceTd">

DisplayQuantity

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

Specifies the maximum amount to display on the book at any one time.

</td>

<td class="confluenceTd">

N

</td>

</tr>

<tr>

<td class="confluenceTd">

LimitPrice

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The price the order is for. Optional for Market Orders.

</td>

<td class="confluenceTd">

N

</td>

</tr>

<tr>

<td class="confluenceTd">

OrderIdOCO

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

Not Used.

</td>

<td class="confluenceTd">

N

</td>

</tr>

<tr>

<td class="confluenceTd">

OrderType

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

"Market", "Limit", "StopMarket", "StopLimit", "TrailingStopMarket", "TrailingStopLimit", "BlockTrade"

</td>

<td class="confluenceTd">

Y

</td>

</tr>

<tr>

<td class="confluenceTd">

PegPriceType

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

Describes how a trailing price is calculated. Options: "Last", "Bid", "Ask", "Midpoint"

</td>

<td class="confluenceTd">

N

</td>

</tr>

<tr>

<td class="confluenceTd">

InstrumentId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

Specifies the Instrument this order is for.

</td>

<td class="confluenceTd">

Y

</td>

</tr>

<tr>

<td class="confluenceTd">

TrailingAmount

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The distance from the market price to trail by, used only for Trailing orders.

</td>

<td class="confluenceTd">

N

</td>

</tr>

<tr>

<td class="confluenceTd">

LimitOffset

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The offset to place a Limit order at when the trailing price is crossed. Used only in TrailingStopLimit orders.

</td>

<td class="confluenceTd">

N

</td>

</tr>

<tr>

<td class="confluenceTd">

Side

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

"Buy" or "Sell"

</td>

<td class="confluenceTd">

Y

</td>

</tr>

<tr>

<td class="confluenceTd">

StopPrice

</td>

<td class="confluenceTd">

decimal

</td>

<td class="confluenceTd">

The price a Stop order is to be placed at once triggered.

</td>

<td class="confluenceTd">

N

</td>

</tr>

<tr>

<td class="confluenceTd">

TimeInForce

</td>

<td class="confluenceTd">

string

</td>

<td class="confluenceTd">

"GTC", "IOC", "FOK"

</td>

<td class="confluenceTd">

Y

</td>

</tr>

<tr>

<td class="confluenceTd">

OMSId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The Order Management System the Account and Instrument reside on. Generally the same as the OMSId returned by AuthenticateUser.

</td>

<td class="confluenceTd">

Y

</td>

</tr>

</tbody>

</table>

##### Response Payload

<table class="wysiwyg-macro" data-macro-name="code" data-macro-id="feb19da4-2dcb-4308-b2bb-35069e07dbbe" data-macro-parameters="language=js" data-macro-schema-version="1" style="background-image: url(https://alphapoint.atlassian.net/wiki/plugins/servlet/confluence/placeholder/macro-heading?definition=e2NvZGU6bGFuZ3VhZ2U9anN9&amp;locale=en_US&amp;version=2); background-repeat: no-repeat;" data-macro-body-type="PLAIN_TEXT">

<tbody>

<tr>

<td class="wysiwyg-macro-body">

<pre>{
	"ReplacementOrderId": 15068,
	"ReplacementClOrdId": 0,
	"OrigOrderId": 15067,
	"OrigClOrdId": 0
}</pre>

</td>

</tr>

</tbody>

</table>

## CancelOrder

#### POST

##### Headers

*   Content-Type=application/json

*   APToken=[Token string supplied in AuthenticateUser Response]

##### Body

<table class="wysiwyg-macro" data-macro-name="code" data-macro-id="f0d6a622-ea7f-48ef-adee-95991329da87" data-macro-parameters="language=js" data-macro-schema-version="1" style="background-image: url(https://alphapoint.atlassian.net/wiki/plugins/servlet/confluence/placeholder/macro-heading?definition=e2NvZGU6bGFuZ3VhZ2U9anN9&amp;locale=en_US&amp;version=2); background-repeat: no-repeat;" data-macro-body-type="PLAIN_TEXT">

<tbody>

<tr>

<td class="wysiwyg-macro-body">

<pre>{
  "OMSId": 1,
  "AccountId": 4,
  "ClOrderId": 0,
  "OrderId": 15068
}</pre>

</td>

</tr>

</tbody>

</table>

<table data-layout="default" class="confluenceTable"><colgroup><col style="width: 170.0px;"><col style="width: 170.0px;"><col style="width: 170.0px;"><col style="width: 170.0px;"></colgroup>

<tbody>

<tr>

<th class="confluenceTh">

Field

</th>

<th class="confluenceTh">

Type

</th>

<th class="confluenceTh">

Description

</th>

<th class="confluenceTh">

Required

</th>

</tr>

<tr>

<td class="confluenceTd">

OMSId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The Order Management System the Account and Instrument reside on. Generally the same as the OMSId returned by AuthenticateUser.

</td>

<td class="confluenceTd">

Y

</td>

</tr>

<tr>

<td class="confluenceTd">

AccountId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The AccountId to submit this order on.

</td>

<td class="confluenceTd">

Y

</td>

</tr>

<tr>

<td class="confluenceTd">

ClOrderId

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

The Client Order Id of the Order to Cancel. You must submit either ClOrderId or OrderId.

</td>

<td class="confluenceTd">

Conditional

</td>

</tr>

<tr>

<td class="confluenceTd">

OrderId

</td>

<td class="confluenceTd">

long

</td>

<td class="confluenceTd">

The Server Order Id of the Order to modify. You must submit either OrderId or ClOrderId.

</td>

<td class="confluenceTd">

Conditional

</td>

</tr>

</tbody>

</table>

##### Response Payload

<table class="wysiwyg-macro" data-macro-name="code" data-macro-id="0e3c43c8-fa2f-4409-a4e1-a3817707f271" data-macro-parameters="language=js" data-macro-schema-version="1" style="background-image: url(https://alphapoint.atlassian.net/wiki/plugins/servlet/confluence/placeholder/macro-heading?definition=e2NvZGU6bGFuZ3VhZ2U9anN9&amp;locale=en_US&amp;version=2); background-repeat: no-repeat;" data-macro-body-type="PLAIN_TEXT">

<tbody>

<tr>

<td class="wysiwyg-macro-body">

<pre>{
	"result": true,
	"errormsg": null,
	"errorcode": 0,
	"detail": null
}</pre>

</td>

</tr>

</tbody>

</table>

## CancelAllOrders

#### POST

##### Headers

*   Content-Type=application/json

*   APToken=[Token string supplied in AuthenticateUser Response]

##### Body

<table class="wysiwyg-macro" data-macro-name="code" data-macro-id="5e1aa921-0c48-4a60-a3c7-cf5ecbc9f613" data-macro-parameters="language=js" data-macro-schema-version="1" style="background-image: url(https://alphapoint.atlassian.net/wiki/plugins/servlet/confluence/placeholder/macro-heading?definition=e2NvZGU6bGFuZ3VhZ2U9anN9&amp;locale=en_US&amp;version=2); background-repeat: no-repeat;" data-macro-body-type="PLAIN_TEXT">

<tbody>

<tr>

<td class="wysiwyg-macro-body">

<pre>{ 
    "AccountId": 4, 
    "OMSId": 1, 
    "InstrumentId": 1 
}</pre>

</td>

</tr>

</tbody>

</table>

<table data-layout="default" class="confluenceTable"><colgroup><col style="width: 170.0px;"><col style="width: 170.0px;"><col style="width: 170.0px;"><col style="width: 170.0px;"></colgroup>

<tbody>

<tr>

<th class="confluenceTh">

Field

</th>

<th class="confluenceTh">

Type

</th>

<th class="confluenceTh">

Description

</th>

<th class="confluenceTh">

Required

</th>

</tr>

<tr>

<td class="confluenceTd">

OMSId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The Order Management System the Account and Instrument reside on. Generally the same as the OMSId returned by AuthenticateUser.

</td>

<td class="confluenceTd">

Y

</td>

</tr>

<tr>

<td class="confluenceTd">

AccountId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The AccountId to submit this order on.

</td>

<td class="confluenceTd">

Y

</td>

</tr>

<tr>

<td class="confluenceTd">

InstrumentId

</td>

<td class="confluenceTd">

integer

</td>

<td class="confluenceTd">

The Instrument to cancel all open orders for.

</td>

<td class="confluenceTd">

Y

</td>

</tr>

</tbody>

</table>

##### Response Payload

<table class="wysiwyg-macro" data-macro-name="code" data-macro-id="80075448-7999-4cc0-947b-3aff2baedd73" data-macro-parameters="language=js" data-macro-schema-version="1" style="background-image: url(https://alphapoint.atlassian.net/wiki/plugins/servlet/confluence/placeholder/macro-heading?definition=e2NvZGU6bGFuZ3VhZ2U9anN9&amp;locale=en_US&amp;version=2); background-repeat: no-repeat;" data-macro-body-type="PLAIN_TEXT">

<tbody>

<tr>

<td class="wysiwyg-macro-body">

<pre>{
	"result": true,
	"errormsg": null,
	"errorcode": 0,
	"detail": null
}</pre>

</td>

</tr>

</tbody>

</table>

* * *

For assistance with Rest API, please contact [support@ndax.io](mailto:support@ndax.io)
