---

title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - json

toc_footers:
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes: # api - group - category - call
  - background/api_bkg_background
  - users/api_users_divider
  - users/api_users_act_activate2fa
  - users/api_users_user_adduseraffiliatetag
  - users/api_users_auth_authenticate2fa
  - users/api_users_auth_authenticateuser
  - users/api_users_user_canceluserreport
  - users/api_users_user_getl2snapshot
  - users/api_users_user_getlevel1
  - users/api_users_user_getuseraccountinfos
  - users/api_users_user_getuseraccounts
  - users/api_users_user_getuseraffiliatecount
  - users/api_users_user_getuseraffiliatetag
  - users/api_users_system_getuserconfig
  - users/api_users_system_getallunredacteduserconfigsforuser
  - users/api_users_system_getunredacteduserconfigbykey
  - users/api_users_system_getuserdevices
  - users/api_users_user_getuserreporttickets
  - users/api_users_user_getuserreportwriterresultrecords
  - users/api_users_system_getvalidate2farequiredendpoints
  - users/api_users_auth_logout
  - users/api_users_system_registernewdevice
  - users/api_users_user_subscribeaccountevents
  - users/api_users_user_subscribelevel1
  - users/api_users_user_subscribelevel2
  - users/api_users_user_subscribeticker
  - users/api_users_user_subscribetrades
  - users/api_users_user_subscribeblocktrades
  - users/api_users_user_unsubscribeblocktrades
  - users/api_users_user_unsubscribelevel1
  - users/api_users_user_unsubscribelevel2
  - users/api_users_user_unsubscribeticker
  - users/api_users_user_unsubscribetrades
  - users/api_users_user_updateuseraffiliatetag
  - users/api_users_system_validate2fa
  - accounts/api_accts_divider
  - accounts/api_accts_user_generatetradeactivityreport
  - accounts/api_accts_user_generatetransactionactivityreport
  - accounts/api_accts_user_generatetreasuryactivityreport
  - accounts/api_accts_user_getaccountinfo
  - accounts/api_accts_user_getaccountpositions
  - accounts/api_accts_user_gettreasuryproductsforaccount
  - accounts/api_accts_user_scheduletradeactivityreport
  - accounts/api_accts_user_scheduletransactionactivityreport
  - accounts/api_accts_user_scheduletreasuryactivityreport
  - trades/api_trades_divider
  - trades/api_trades_user_getaccounttrades
  - trades/api_trades_user_getaccounttransactions
  - trades/api_trades_user_getopentradereports
  - trades/api_trades_user_getallopentradereports
  - trades/api_trades_user_gettickerhistory
  - trades/api_trades_user_gettradeshistory
  - oms_orders/api_omsord_divider
  - oms_orders/api_omsord_user_cancelallorders
  - oms_orders/api_omsord_user_cancelorder
  - oms_orders/api_omsord_user_cancelquote
  - oms_orders/api_omsord_user_cancelreplaceorder
  - oms_orders/api_omsord_user_createquote
  - oms_orders/api_omsord_user_getopenorders
  - oms_orders/api_omsord_user_getopenquotes
  - oms_orders/api_omsord_user_getorderfee
  - oms_orders/api_omsord_user_getorderhistory
  - oms_orders/api_omsord_user_getorderhistorybyorderid
  - oms_orders/api_omsord_user_getordershistory
  - oms_orders/api_omsord_user_getorderstatus
  - oms_orders/api_omsord_user_modifyorder
  - oms_orders/api_omsord_user_sendorder
  - oms_orders/api_omsord_user_updatequote
  - products/api_products_divider
  - products/api_prods_user_getproduct
  - products/api_prods_user_getproducts
  - instrs/api_instrs_divider
  - instrs/api_instrs_user_getinstrument
  - instrs/api_instrs_user_getinstruments
  - tickets/api_tickets_divider
  - tickets/api_tix_system_cancelwithdraw
  - tickets/api_tix_system_createdepositticket
  - tickets/api_tix_system_createwithdrawticket
  - tickets/api_tix_user_getaccountdeposittransactions
  - tickets/api_tix_user_getaccountwithdrawtransactions
  - tickets/api_tix_system_getalldepositrequestinfotemplates
  - tickets/api_tix_system_getdepositinfo
  - tickets/api_tix_system_getdepositrequestinfotemplate
  - tickets/api_tix_system_getdeposits
  - tickets/api_tix_system_getdepositticket
  - tickets/api_tix_system_getdeposittickets
  - tickets/api_tix_system_getomswithdrawfees
  - tickets/api_tix_user_getwithdrawfee
  - tickets/api_tix_system_getwithdraws
  - tickets/api_tix_system_getwithdrawtemplate
  - tickets/api_tix_system_getwithdrawtemplatetypes
  - tickets/api_tix_system_getwithdrawticket
  - tickets/api_tix_system_getwithdrawtickets
  - tickets/api_tix_system_submitdepositticketcomment
  - tickets/api_tix_system_submitwithdrawticketcomment
  - uncertain/api_uncertain_divider
  - uncertain/api_uncert_user_ping

  
  # - apad-markdown-documentation/api_apad_divider
  # - apad-markdown-documentation/api_apad_background
  # - apad-markdown-documentation/api_apad_clawbackshares
  # - apad-markdown-documentation/api_apad_createasset
  # - apad-markdown-documentation/api_apad_createcoadmin
  # - apad-markdown-documentation/api_apad_createcompany
  # - apad-markdown-documentation/api_apad_createcompanywithexistinguser
  # - apad-markdown-documentation/api_apad_createcompanywithuser
  # - apad-markdown-documentation/api_apad_createuser
  # - apad-markdown-documentation/api_apad_createuseragent
  # - apad-markdown-documentation/api_apad_createusercoshareholder
  # - apad-markdown-documentation/api_apad_getassets
  # - apad-markdown-documentation/api_apad_getcompanies
  # - apad-markdown-documentation/api_apad_getuserfromsession
  # - apad-markdown-documentation/api_apad_getusers
  # - apad-markdown-documentation/api_apad_removeallcoadmins
  # - apad-markdown-documentation/api_apad_removeuserrole
  # - apad-markdown-documentation/api_apad_setassetaccessforuser
  # - apad-markdown-documentation/api_apad_transferasset
  # - apad-markdown-documentation/api_apad_updatecompanyaddroles
  # - apad-markdown-documentation/api_apad_updateuser
  # - apad-markdown-documentation/api_apad_version
  # - digitizer/api_digitizer_doc
 


 
search: true
---

# Introduction

This API covers the User-category calls in **version 3.3** of the AlphaPoint Exchange software. It includes calls required for log-in and authentication.

The calls have been organized roughly to correspond to similar functions you would find in the AlphaPoint Admin. For example, in the Admin you manage users in the Users function. So calls that manage users have been gathered in the Users section of the API.


## 3.4.1 New Endpoints
**RegisterNewDevice**

**GetUserDevices**

**GetValidate2FARequiredEndpoints**

**Validate2FA**

## Revised Calls 3.4.1

**SendOrder**

Request Payload changed for Market Buy Value - if Buy order and Value (decimal) parameter is supplied, the Market order will execute up to the value specified.

**GetExchangeServiceIds**
>Old GetExchangeServiceIDs Response
An array of strings representing service ids.

>New GetExchangeServiceIds Response
Array hard coded with a single entry: "Matching Engine"

```json
[
    {
        "Name": "V2ExchangeCore|1",
        "ServiceId": "Matching Engine"
        "URI": null
    }
]
```

**GetExchanges**
>Old GetExchangeServiceIds Response
A list of exchanges within a specified exchange service id.

>New GetExchangeServiceIds Response
Retrieves exchanges from "THE" mathcing engine as there can only ever be one as of 3.4

**Validate2FA**

Behavior change, no longer has public permissions specified. 

**AddInstrument (DEPRECATED)**

Behavior change, endpoint returns with bad request message specifying the endpoint is deprecated. 

**UpdateInstrument (DEPRECATED)**

Behavior change, endpoint returns with bad request message specifying the endpoint is deprecated. 

**RemoveOperatorUser**

Behavior change from “Deprecated” to “Remove Association of Operator with User" 


## 3.5.0 Behavior Changes

**API Behavior Changes**

Any query APIs that return these objects now have the below new fields and response value changes as listed.

**AccountPosition**

| Key                 | Value                                                        |
| ------------------- | ------------------------------------------------------------ |
| NotionalHoldAmount| **decimal.** Cross Product Amount on Hold from open orders |
| NotionalRate | **decimal.** Current notional rate from base currency |
| TotalDayDepositNotional | **decimal.** Total Calendar Day Deposit Notional |
| TotalMonthDepositNotional | **decimal.** Total Calendar Month Deposit Notional |
| TotalDayWithdrawNotional | **decimal.** Total Calendar Day Withdraw Notional |
| TotalMonthWithdrawNotional | **decimal.** Total Calendar Month Withdraw Notional |

**OrderTrade**

| Key                 | Value                                                        |
| ------------------- | ------------------------------------------------------------ |
| CounterPartyClientUserId| **int.** Indicates counterparty source of trade (OMS, Remarketer, FIX) |
| NotionalProductId | **int.** Notional product the notional value was captured in |
| NotionalRate | **decimal.** Notional rate from base currency at time of trade |
| NotionalValue | **decimal.** Notional value in base currency of venue at time of trade |

**AccountInstrumentStatistics**

| Key                 | Value                                                        |
| ------------------- | ------------------------------------------------------------ |
| NotionalProductId | **int.** Notional product the notional value was captured in |
| DailyNotionalTradeVolume | **decimal.** Total Calendar Day Trading Notional |
| MonthlyNotionalTradeVolume | **decimal.** Total Calendar Month Trading Notional |
| YearlyNotionalTradeVolume | **decimal.** Total Calendar Year Trading Notional |

**VerificationLevelInstruments**

| Key                 | Value                                                        |
| ------------------- | ------------------------------------------------------------ |
| NotionalProductId | **int.** Notional product the notional value was captured in |
| DailyNotionalLimit | **decimal.** Total Calendar Day Trading Notional |
| MonthlyNotionalLimit | **decimal.** Total Calendar Month Trading Notional |
| YearlyNotionalLimit | **decimal.** Total Calendar Year Trading Notional |

**AccountStatistics**

| Key                 | Value                                                        |
| ------------------- | ------------------------------------------------------------ |
| TotalDayDepositNotional | **decimal.** Total Calendar Day Deposit Notional |
| TotalMonthDepositNotional | **decimal.** Total Calendar Month Deposit Notional |
| TotalDayWithdrawNotional | **decimal.** Total Calendar Day Withdraw Notional |
| TotalMonthWithdrawNotional | **decimal.** Total Calendar Month Withdraw Notional |

**VerificationLevelProducts**

| Key                 | Value                                                        |
| ------------------- | ------------------------------------------------------------ |
| DailyDepositNotionalLimit | **decimal.** Total Calendar Day Deposit Notional Limit |
| MonthlyDepositNotionalLimit | **decimal.** Total Calendar Month Deposit Notional Limit |
| DailyWithdrawNotionalLimit | **decimal.** Total Calendar Day Withdraw Notional Limit |
| MonthlyWithdrawNotionalLimit | **decimal.** Total Calendar Month Withdraw Notional Limit |

**OMSInfo**

| Key                 | Value                                                        |
| ------------------- | ------------------------------------------------------------ |
| BaseNotionalProductId | **int.** Id of Base Product to be used in Notional Limits |

**Fee**

| Key                 | Value                                                        |
| ------------------- | ------------------------------------------------------------ |
| FeeTier | **int.** Id of the Fee Tier the fee belongs to. Matches AccountInfo FeeGroupId (previously existing field) |

**Instrument**

| Key                 | Value                                                        |
| ------------------- | ------------------------------------------------------------ |
| PriceCollarIndexDifference | **decimal.** The percent different from the index price that an order is allowed to execute at. Anything falling outside of the index price +/- (1 + PriceCollarIndexDifference) will be collared |
| PriceCollarConvertToOtcEnabled | **bool.** Turns on/off conversion of collared orders to block trades |
| PriceCollarConvertToOtcClientUserId | **int.** Internal System UserId to assign the collared otc orders to. Should alwaays be 1 in current implementation (default) |
| PriceCollarConvertToOtcAccountId | **int.** Account Id to assign the collared orders to. This will effectively be a liability account that will need to have working block trades managed by operator. |
| PriceCollarConvertToOtcThreshold | **decimal.** Threshold of remaining size of order to convert to block trade. If collared order does not have remaining quantity above this threshold the remainder will be cancelled. |
| OtcConvertSizeEnabled | **bool.** Turns on/off auto conversion of 'large' limit orders converted to block trade orders upon receipt by the matching engine |
| OtcConvertSizeThreshold | **decimal.** Threshold to convert limit order quantity to block trade automatically for discovery by block trade market participants |

## Revised Calls 3.5.0

Support for additional fields has been added to the following requests:

 * GetAccounts
 * SubmitBlockTrade
 * ModifyOrder

Additional fields have been added to the following responses:

* GetWithdrawFormTemplateTypes
* SubmitAccountLedgerEntry
* GetAllLedgerEntryTickets
* GetOpenWithdrawHolds
* GetOrderStatus
* TransferFunds
* GetLevel1 / Level1UpdateEvent / SubscribeLevel1

## 3.5.0 New Endpoints

**GetAllAccountsConfigs**

**GetOMSFeeTiers**

**GetAllOpenTradeReports**

**SubscribeBlockTrades**

**UnsubscribeBlockTrades**

