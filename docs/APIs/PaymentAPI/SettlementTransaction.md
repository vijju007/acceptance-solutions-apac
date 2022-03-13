# Settlement Transaction

This API is used to send settlement transaction request. Merchants needs to add session 
token received during login api call in the header of this API.


## Endpoint

`/boardinggateway/cloudpoi/PosPush/nonOpiProcessAmount`

## Payload Example

### Request Payload

```json
{
  "ain": "4700000",
  "functionCode": "12",
  "merchantId": "470000032001091",
  "terminalId": "33533344",
  "customerRefNumber": "77777777777",
  "merchantRefNumber": "Guru483",
  "billerId": "845",
  "convFee": "20",
  "cgst": "16",
  "igst": "14",
  "sgst": "12",
  "totalAmount": "",
  "tranCurrency": "256",
  "reqDate": "26022022",
  "reqTime": "160900",
  "authAmount": "",
  "tranDate": "",
  "tranTime": "",
  "invoiceNumber": "",
  "cardLastNumber": "",
  "callbackURL": "",
  "mrchCountryCode": "",
  "tranType": "",
  "rrn": "",
  "emiRefNumber": "",
  "emiTenure": "",
  "udf1": "",
  "udf2": "",
  "paramList": [
    {
      "param_lit": "param1 key",
      "param": ""
    },
    {
      "param_lit": "param 2 key",
      "param": ""
    }
  ]
}

```
  
***Token should be sent as Authorization.***

### Minimum Requirements

The below table contains the mandatory fields required for a successful request. The full request schemas are available in our [API Explorer](../api/?type=get&path=/boardinggateway/cloudpoi/PosPush/nonOpiProcessAmount).

The below table identifies the required query parameters in the request message.

The below table identifies the required json properties in the request message.
### Request
| Variable | Type | Length |  Mandatory/Optional/Conditional  | Description/Values |
| -------- | :-------: | :--: | :------------: | ------------------ |
| `merchantId` | *string* | 15 | M | Merchant ID assigned. |
| `ain` | *string* | 07 | M | Acquirer institution number. |
| `functionCode` | *string* | 02 | M | 00 = Sale  - Digital and Card|
|  |  |  |  | 01 = "Sale" - Card|
|  |  |  |  | 02 = "Preauth"|
|  |  |  |  | 03 = "Preauth Completion|
|  |  |  |  | 04 = "Refund"|
|  |  |  |  | 12 = "Settlement"|
|  |  |  |  | 11 = "Transaction Status Check" (Inquiry)
|  |  |  |  | 05 = "Void"|
|  |  |  |  | 04 = "efund"|
| `terminalId` | *string* | 07 | M | Terminal ID. |
| `billerId` | *string* | 03 | M | Biller Id provided by Fiserv. |
| `merchantRefNumber` | *string* | 14(BOCM – 50) | M | Unique number for each transaction. Inquiry transaction should have same MRN of original txn. |
| `customerRefNumber` | *string* | 20 | O | Consumer Number |
| `authAmount` | *string* | 19 | M | Bill Amount including decimal (Ex: “50.00” for $50 sale). Send 0.00 for inquiry txn. |
| `convFee` | *string* | 10 | C – To be sent if fee is charged | Convenience Fee including decimal (Ex: "5.00" for $5 fee) |
| `cgst` | *string* | 10 | C – To be sent if CGST is included in the total amount | Central GST Including decimal (Ex: "10.00" for $10 cgst) |
| `igst` | *string* | 10 | C – To be sent if IGST is included in the total amount | State GST Including decimal (Ex: "10.00" for $10 igst) |
| `sgst` | *string* | 10 | C – To be sent if SGST is included in the total amount | State GST Including decimal (Ex: "100.00" for $10 sgst) |
| `totalAmount` | *string* | 19 | M | Total Amount (auth, fee, gsts) including decimal ((Ex: "57.00" for $57 sale). |
| `tranCurrency` | *string* | 03 | M | Transaction Currency Code (3-digit numeric value). |
| `reqDate` | *Date* | DDMMYYYY | M | Transaction initiated Date. |
| `reqTime` | *Timestamp* | HHMMSS | M | Transaction initiated time. |
| `tranDate` | *Date* | DDMMYYYY | C (required for Refund and transaction status check) |Original transaction date. |
| `tranTime` | *Timestamp* | HHMMSS | C (required for Refund and transaction status check) | Original transaction time. |
| `cardLastNumber` | *string* | 04 | C (required for pre auth Completion) | Last 4 Digits of Card Number |
| `cardBin` | *string* | 06 | C (required refund) | First six digits of the Card, used in the original (sale) transaction |
| `callbackURL` | *string* | 100 | O | Response URL, place holder for notification API call feature). |
| `mrchCountryCode` | *string* | 03 | M | Merchant Country Code (3-digit numeric value) |
| `tranType` | *string* | 50 | O | Transaction Description |
| `rrn` | *string* | 20 | C (Mandatory for Refund and optional for Inquiry txn) | Must pass the same value received in original transaction response |
| `emiTenure` | *string* | 02 | C (required for EMI transactions) | EMI duration |
| `paramList` | *array* | NA | O | Biller can pass any additional details if required in arrary format "paramList": [{"param_lit": "param1 key","param": "23"}] |
| `udf1` | *string* | 100 | O | User Defined Field |
| `udf2` | *string* | 100 | O | User Defined Field |

### Successful Response Payload

```json
{
    "functionCode": "12",
    "source": null,
    "billingAmount": null,
    "invoiceNumber": "",
    "customerMobile": null,
    "billingCurrency": "INR",
    "transactionId": "202202265257416",
    "customerName": null,
    "respCode": "200",
    "response": "SUCCESS",
    "cardType": null,
    "rrn": null,
    "authCode": null,
    "merchantId": "470000032001091",
    "terminalId": "33533344",
    "respMsg": "Transaction Success",
    "amexSeNumber": "",
    "emiTenure": "",
    "emiInterestRate": "",
    "emiProcessingFee": "0",
    "emiDiscAmt": "0",
    "dccIndicator": "0",
    "dccExchangeRate": "",
    "offlineFlag": "N",
    "cardLastNumber": "",
    "totalAmount": "0.00",
    "merchantRefNumber": "Guru483",
    "customerRefNumber": "77777777777",
    "emiFlag": "",
    "cardNumber": null,
    "expDate": "",
    "posEntryMode": "",
    "walletType": "",
    "primaryId": "",
    "custId": "",
    "emiPerMonth": "0",
    "tranDate": "26022022",
    "tranTime": "",
    "cardBin": null,
    "tipAmount": null,
    "settlementDetails": "NON-OPI VISA CARD 2  1,321.50 TIP 2 71.50 MASTERCARD 3  400.00",
    "walletId": ""
}
```

### Error Response Payload

```json
{
  "status": {
    "statusCode": 401,
    "message": "Token not found"
  }
}
```

### Response
| Variable | Type | Length |  Mandatory/Optional/Conditional  | Description/Values |
| -------- | :-------: | :--: | :------------: | ------------------ |
| `merchantId` | *string* | 20 | M | Merchant ID |
| `transactionId` | *string* | 20 | M | Unique Id (Biller tran details table) |
| `functionCode` | *string* | 02 | M | Same as request |
| `invoiceNumber` | *string* | 20 | O | Terminal Invoice Number |
| `cardLastNumber` | *string* | 4 | C (required for Pre-auth) | Last 4 Digits of Card Number |
| `totalAmount` | *string* | 19 | M | Total Amount (auth, fee, gsts, tip) including decimal ((Ex: “57.00” for $57 sale |
| `tipAmount` | *string* | 10 | C – To be sent in response if Tip is included | Tip Amount including decimal (Ex: “7.00” for $7 tip)|
| `merchantRefNumber` | *string* | 14 | M | Merchant Reference Number |
| `customerRefNumber` | *string* | 20 | 0 | Custmer Reference Number |
| `respCode` | *string* | 05 | M | 200/300/actual switch response |
| `response` | *string* | 20 | M | SUCCESS/FAILURE |
| `respMsg` | *string* | 20 | O | Error Message |
| `authCode` | *string* | 06 | C (will be populated with Null for time out response) | Received from Issuer Host |
| `rrn` | *string* | 20 | C (will be populated with Null for time out response) | Received from Issuer Host |
| `cardBin` | *string* | 06 | O | Card Bin |
| `dccIndicator` | *string* | 01 | M | 0 – Non DCC, 1 – DCC  |
| `billingCurrency` | *string* | 03 | C | DCC currency code |
| `billingAmount` | *string* | 19 | C | DCC amount |
| `dccExchangeRate` | *string* | 20 | M | Currency exchange rate |
| `amexSeNumber` | *string* | 10 | C | Applicable for AMEX transaction |
| `emiFlag` | *string* | 01 | M | 0 – Non-EMI 1 - EMI |
| `emiTenure` | *string* | 02 | C | Applicable for EMI transaction |
| `emiInterestRate` | *string* | 10 | C | Applicable for EMI transaction |
| `emiProcessingFee` | *string* | 10 | C | Applicable for EMI transaction |
| `emiDiscAmt` | *string* | 10 | C | Applicable for EMI transaction |
| `emiPerMonth` | *string* | 10 | C | Applicable for EMI transaction |
| `cardNumber` | *string* | 19 | O | Card Number |
| `expDate` | *string* | 4 | O |  |
| `posEntryMode` | *string* | 10 | M | MANUAL / SWIPE / INSERT / CLSS / FALLBACK / CLSS_MSR / QRC |
| `walletType` | *string* | 10 | C – Digital transactions | Type of wallet used such as UPI, Amazon Pay LPM name |
| `primaryId` | *string* | 20 | C - Digital transactions | Reference Number of the QR Request |
| `custId` | *string* | 35 | O | Customer identifier,Vehicle number for fasttag VPA for UPI QR |
| `walletId` | *string* | 05 | O | Unique wallet ID associated with each wallet |
| `Source` | *string* | 20 | O | Transaction Initiated source |
| `customerMobile` | *string* | 20 | O | Customer Mobile Number |
| `customerName` | *string* | 20 | O | Cardholder Name |
| `cardType` | *string* | 5 | O | Card Type |
| `offlineFlag` | *string* | 01 | O | offline flag |
| `tranDate` | *date* | DDMMYYYY | O | transaction date |
| `tranTime` | *string* | HHMMS | O | transaction time |
| `settlementDetails` | *string* | 2000 | O | set settlement Details |




Below table provides the list of application's error code and its description.

| ErrorCode |  Description/Values |
| --------  | ------------------ |
|`401` |Token not found|  
|`200` |Success|
|`300` |Request Failure|
|`500` |Internal Server Error|
|`404` |Not Found|
|`502` |Request Timed Out|