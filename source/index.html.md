---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://beta.inkredo.in/auto/signup'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Inkredo API!
You must be a premium customer to use the api

# Authentication

Inkredo uses API keys to allow access to the API. You can register a new Inkerdo API key at our [main webapp](https://beta.inkredo.in).
After completing the KYC process and subscribing to our services, you can to to the settings page and obtain the keys from the api section

Inkredo expects for the API key to be included in all API requests to the server in a header that looks like the following:

`access-id: iidd`

`access-key: kkeeyy`

<aside class="notice">
You must replace <code>iidd</code> and <code>kkeeyy</code> with your personal access-key and access-id.
</aside>

# Bank statement analysis

## Create borrower

```shell
curl --request POST \
  --url https://beta.inkredo.in/api/v0/dashboard/create_borrower/ \
  --header 'Content-Type: application/json' \
  --header 'access-id: iidd' \
  --header 'access-key: kkeeyy' \
  --data '{"name":"Ram Yadav"}'
```

> The above command returns JSON structured like this:

```json
{
    "success": true,
    "message": "Borrower created successfully",
    "borrowerId": "5bb36bc3e38eb85f7207461d"
}
```

This endpoint creates a new borrower. You need to save this borrowerId for later use.

### HTTP Request

`POST https://beta.inkredo.in/api/v0/dashboard/create_borrower`

### Headers
Name | Value
---|---
Content-Type | application/json
access-id | iidd
access-key | kkeeyy


### Body

Parameter | Required | Description
--------- | ------- | -----------
name | true | Name of the borrower


## Supported banks

```shell
curl --request GET \
  --url https://beta.inkredo.in/api/v0/parser/supported_banks \
  --header 'Content-Type: application/json' \
  --header 'access-id: iidd' \
  --header 'access-key: kkeeyy'
```

> The above command returns JSON structured like this:

```json
{
    "banks": [
        {
            "code": "HDFC",
            "inputs": {
                "csv": true,
                "pdf": true,
                "xls": true,
                "xlsx": true
            },
            "name": "HDFC Bank"
        },
        {
            "code": "ICICI",
            "inputs": {
                "csv": false,
                "pdf": true,
                "xls": false,
                "xlsx": false
            },
            "name": "ICICI Bank"
        },
    ]
}       
```

This endpoint retrieves a list of all banks with information on the file type currently supported.

### HTTP Request

`GET https://beta.inkredo.in/api/v0/parser/supported_banks`

### Headers
Name | Value
---|---
Content-Type | application/json
access-id | iidd
access-key | kkeeyy


## Parser

> The above command returns JSON structured like this:

```json
{
  "data": {
    "meta": {
      "speed": {
        "external": {
          "analysis": 1210,
          "parsing": 21680,
          "statementFetch": 1460
        },
        "internal": {
          "analysis": 16.157966,
          "convertToExcel": 4196.096221,
          "convertToStaticReport": 117.315543
        }
      }
    },
    "allTransactions": [
      {
        "balanceAmount": 1000,
        "category": [
          "Transfer",
          "Debit"
        ],
        "date": "02/01/17",
        "depositAmount": 0,
        "particular": "NEFT D",
        "reference": "N00217088",
        "type": "DEBIT",
        "withdrawalAmount": 5000
      },
      {
        "balanceAmount": 8141.11,
        "category": [
          "Transfer",
          "Earning"
        ],
        "date": "02/01/17",
        "depositAmount": 313,
        "particular": "NEFT CR-",
        "reference": "0P17010247110093",
        "type": "CREDIT",
        "withdrawalAmount": 0
      }
    ],
    "summary": {
      "credit": {
        "amount": 5510.10,
        "count": 221
      },
      "debit": {
        "amount": 55651.28,
        "count": 203
      },
      "defaults": {
        "amount": 4201.28,
        "count": 4
      }
    },
    "topCredits": [
      {
        "amount": 60000,
        "date": "08 Feb 17",
        "particular": "NEFT XXX",
        "balanceAmount": 63131,
        "category": [
          "Transfer",
          "Credit"
        ]
      },
      {
        "amount": 50000,
        "date": "08 Mar 17",
        "particular": "IMPS-YYY",
        "balanceAmount": 53785,
        "category": [
          "Transfer",
          "Earning"
        ]
      }
    ],
    "topDebits": [
      {
        "amount": 26104,
        "date": "08 Mar 17",
        "particular": "IB BILLPAY ",
        "balanceAmount": 27681,
        "category": [
          "Payment"
        ]
      },
      {
        "amount": 17662,
        "date": "25 Mar 17",
        "particular": "NFXXX/MAKEMYTRIP",
        "balanceAmount": 4185,
        "category": [
          "Travel"
        ]
      }
    ],
    "recurringCredits": {
      "data": [
        {
          "summary": "ani technologies",
          "balanceAmount": 8141.11,
          "date": "02/01/17",
          "particular": "NEFT CR-XXX-ANI TECHNOLOGIES PRIVATE LIMITED-XXX",
          "amount": 313
        },
        {
          "summary": "ani technologies",
          "balanceAmount": 16911.11,
          "date": "03/01/17",
          "particular": "NEFT CR-XXX-ANI TECHNOLOGIES PRIVATE LIMITED-XXX",
          "amount": 9280
        }
      ],
      "lastTransactionDate": "29/06/17",
      "uniqueOccurrences": 9,
      "duration": 6
    },
    "recurringDebits": {
      "data": [
        {
          "summary": "irctc_new",
          "balanceAmount": 20594.19,
          "date": "12/01/17",
          "particular": "XXX/IRCTC_NEW",
          "amount": 620
        },
        {
          "summary": "irctc_new",
          "balanceAmount": 20582.69,
          "date": "12/01/17",
          "particular": "XXX/IRCTC_NEW",
          "amount": 11.5
        }
      ],
      "lastTransactionDate": "29/06/17",
      "uniqueOccurrences": 23,
      "duration": 6
    },
    "runningLoans": {
      "loansByName": {
        "1834": {
          "color": "#ec8b63",
          "name": "BAJAJ FINEMI",
          "numberOfInstallments": 3,
          "totalAmountPaid": 5502,
          "numberOfDefaults": 0
        },
        "4500": {
          "color": "#008fba",
          "name": "BAJAJFINEMI",
          "numberOfInstallments": 4,
          "totalAmountPaid": 18000,
          "numberOfDefaults": 1
        },
        "14400": {
          "color": "#3944a0",
          "name": "ACH ",
          "numberOfInstallments": 5,
          "totalAmountPaid": 72000,
          "numberOfDefaults": 1
        }
      },
      "loansByMonth": [
        {
          "14400": 14400,
          "month": "17/01"
        },
        {
          "14400": 14400,
          "month": "17/02"
        },
        {
          "4500": 4500,
          "14400": 14400,
          "month": "17/03"
        },
        {
          "1834": 1834,
          "4500": 4500,
          "14400": 14400,
          "month": "17/04"
        }
      ],
      "allLoanTransactions": [
        {
          "date": "23/06/17",
          "loanAmount": 14400,
          "balanceAmount": 1080.2,
          "particular": "ACH D- AUFINANCIERS-XXX",
          "type": "DEBIT"
        },
        {
          "date": "05/06/17",
          "loanAmount": 4500,
          "balanceAmount": 755.22,
          "particular": "BAJAJ FINEMI-BF-XXX",
          "type": "DEBIT"
        },
        {
          "date": "02/06/17",
          "loanAmount": 1834,
          "balanceAmount": 1783.22,
          "particular": "BAJAJ FINEMI-BF-X",
          "type": "DEBIT"
        }
      ]
    },
    "defaults": {
      "summary": {
        "amount": 5000,
        "count": 2
      },
      "allDefaults": [
        {
          "balanceAmount": 131.32,
          "date": "08/02/17",
          "defaultAmount": 2500,
          "particular": "CC XX AUTOPAY SI-TAD",
          "category": [
            "Payment",
            "Credit Card"
          ]
        },
        {
          "balanceAmount": 250,
          "date": "08/03/17",
          "defaultAmount": 2500,
          "particular": "CC XX AUTOPAY SI-TAD",
          "category": [
            "Payment",
            "Credit Card"
          ]
        }
      ]
    },
    "monthlyAverageBalance": [
      {
        "average": 10553,
        "endDate": 31,
        "monthKey": "17/01",
        "startDate": 2
      },
      {
        "average": 10463,
        "change": {
          "amount": -90,
          "percent": "-0.85"
        },
        "endDate": 28,
        "monthKey": "17/02",
        "startDate": 1
      }
    ],
    "mode": "full"
  },
  "success": true,
  "message": "Statement parsed"
}
```
This endpoint parsers and analysis a bank statement

### HTTP Request

`POST https://beta.inkredo.in/api/v0/parser/`

### Headers
Name | Value
---|---
Content-Type | application/x-www-form-urlencoded
access-id | iidd
access-key | kkeeyy



### Body
Parameter | Required | Description
--------- | ------- | -----------
bank | true | bank code obtained from supported banks api above
statement | true | bank statement file to be analysed
borrowerId | true | id of the borrower created earlier

## Reanalyse bank statement
`POST https://beta.inkredo.in/api/v0/parser/reanalyse/`

### Body
`{"borrowerId":"5bb20ba98b583b0b9cf1e13b"}`

### Headers
Name | Value
---|---
Content-Type | application/json
access-id | iidd
access-key | kkeeyy

### Response
same as the parser api



