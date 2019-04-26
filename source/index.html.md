---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://beta.inkredo.in/auth/signup'>Sign Up for a Developer Key</a>
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
After completing the KYC process and subscribing to our services, you can go to the settings page and obtain the keys from the api section

Inkredo expects the API key to be included in all API requests to the server in a header that looks like the following:

`access-id: your_access_id`

`access-key: your_access_key`

<aside class="notice">
You must replace <code>your_access_id</code> and <code>your_access_key</code> with your personal access-key and access-id.
</aside>

# Bank statement analysis

## Create borrower

```shell
curl --request POST \
  --url https://beta.inkredo.in/api/v0/dashboard/create_borrower/ \
  --header 'Content-Type: application/json' \
  --header 'access-id: your_access_id' \
  --header 'access-key: your_access_key' \
  --data '{"name":"Ram GANDHI"}'
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
access-id | your_access_id
access-key | your_access_key


### Body

Parameter | Required | Description
--------- | ------- | -----------
name | true | Name of the borrower


## Supported banks

```shell
curl --request GET \
  --url https://beta.inkredo.in/api/v0/parser/supported_banks \
  --header 'Content-Type: application/json' \
  --header 'access-id: your_access_id' \
  --header 'access-key: your_access_key'
```

> The above command returns JSON structured like this:

```json
{
    "banks": [
        {
            "code": "HDFC",
            "displayName": "HDFC Bank",
            "support": {
                "csv": true,
                "excel": true,
                "pdf": true
            }
        },
        {
            "code": "ICICI",
            "name": "ICICI Bank",
            "inputs": {
                "csv": false,
                "excel": false,
                "pdf": true
            }
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
access-id | your_access_id
access-key | your_access_key


## Parser

> The above command returns JSON structured like this:

```json
{
        "allTransactions": [
            {
                "balanceAmount": 7828.11,
                "category": [
                    "Transfer",
                    "Debit"
                ],
                "date": "02/01/17",
                "depositAmount": 0,
                "isAutoDebit": false,
                "particular": "NEFT DR-IDIB000S209-ADITYA RATHI-NETBANK, MUM-N002170226538872",
                "reference": "N00132226538872",
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
                "isAutoDebit": false,
                "particular": "NEFT CR-YESB0000002-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17010247110013",
                "reference": "0P11341024715009",
                "type": "CREDIT",
                "withdrawalAmount": 0
            },
            {
                "balanceAmount": 7631.11,
                "category": [
                    "Travel",
                    "Gas Station"
                ],
                "date": "03/01/17",
                "depositAmount": 0,
                "isAutoDebit": false,
                "particular": "POS 422112XXXXXX1221 RATHI PETRO POS DEBIT",
                "reference": "000099819958077",
                "type": "DEBIT",
                "withdrawalAmount": 510
            },
            {
                "balanceAmount": 16911.11,
                "category": [
                    "Transfer",
                    "Earning"
                ],
                "date": "03/01/17",
                "depositAmount": 9280,
                "isAutoDebit": false,
                "particular": "NEFT CR-YESB0000102-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDI-0P170103481888289",
                "reference": "0P17010348417669",
                "type": "CREDIT",
                "withdrawalAmount": 0
            },
            {
                "balanceAmount": 13911.11,
                "category": [
                    "Shops"
                ],
                "date": "03/01/17",
                "depositAmount": 0,
                "isAutoDebit": false,
                "particular": "POS 4303XXXXXX11211 PAYTM MOBILE SOL POS DEBIT",
                "reference": "0000700314344623",
                "type": "DEBIT",
                "withdrawalAmount": 3000
            },
            {
                "balanceAmount": 10911.11,
                "category": [
                    "Transfer",
                    "Debit"
                ],
                "date": "04/01/17",
                "depositAmount": 0,
                "isAutoDebit": false,
                "particular": "NEFT DR-IDIB000S118-ADITHYA RATHI-NETBANK, MUM-N004170113147394",
                "reference": "N004170113147394",
                "type": "DEBIT",
                "withdrawalAmount": 3000
            },
            {
                "balanceAmount": 11290.11,
                "category": [
                    "Transfer",
                    "Earning"
                ],
                "date": "05/01/17",
                "depositAmount": 4879,
                "isAutoDebit": false,
                "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17010549892717",
                "reference": "0P17010549892717",
                "type": "CREDIT",
                "withdrawalAmount": 0
            },
                       {
                "balanceAmount": 3903.2,
                "category": [
                    "Transfer",
                    "Earning"
                ],
                "date": "27/06/17",
                "depositAmount": 445,
                "isAutoDebit": false,
                "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N178170029357228",
                "reference": "N178170029357228",
                "type": "CREDIT",
                "withdrawalAmount": 0
            },
            {
                "balanceAmount": 6182.2,
                "category": [
                    "Transfer",
                    "Earning"
                ],
                "date": "28/06/17",
                "depositAmount": 2279,
                "isAutoDebit": false,
                "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N179170029675270",
                "reference": "N179170029675270",
                "type": "CREDIT",
                "withdrawalAmount": 0
            },
            {
                "balanceAmount": 7347.2,
                "category": [
                    "Transfer",
                    "Credit"
                ],
                "date": "29/06/17",
                "depositAmount": 1165,
                "isAutoDebit": false,
                "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHIROHAN-N999Opening Balance Dr Count Cr Count Debits Credits Closing Bal",
                "reference": “999“,
                "type": "CREDIT",
                "withdrawalAmount": 0
            }
        ],
        "summary": {
            "credit": {
                "amount": 551077.37,
                "count": 221
            },
            "debit": {
                "amount": 556558.28,
                "count": 203
            },
            "defaults": {
                "amount": 42044.28,
                "count": 4
            }
        },
        "topCredits": [
            {
                "amount": 60000,
                "date": "08 Feb 17",
                "particular": "NEFT CR-UCBA0001910-DAYA NAND-ROHAN GANDHI-SAA90378310",
                "balanceAmount": 63131,
                "category": [
                    "Transfer",
                    "Credit"
                ]
            },
            {
                "amount": 50000,
                "date": "08 Mar 17",
                "particular": "IMPS-82777281924-TELE COMMUNICATIO-HDFC--PERSONAL",
                "balanceAmount": 53785,
                "category": [
                    "Transfer",
                    "Earning"
                ]
            },
            {
                "amount": 23000,
                "date": "28 Apr 17",
                "particular": "CASH DEP SOHNA",
                "balanceAmount": 25934,
                "category": [
                    "Cash Advance",
                    "Credit"
                ]
            },
            {
                "amount": 9280,
                "date": "03 Jan 17",
                "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17010348417669",
                "balanceAmount": 16911,
                "category": [
                    "Transfer",
                    "Earning"
                ]
            },
            {
                "amount": 6209,
                "date": "06 Feb 17",
                "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17020678300541",
                "balanceAmount": 6958,
                "category": [
                    "Transfer",
                    "Earning"
                ]
            },
            {
                "amount": 6082,
                "date": "09 Jan 17",
                "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17010953765743",
                "balanceAmount": 13292,
                "category": [
                    "Transfer",
                    "Earning"
                ]
            },
            {
                "amount": 5324,
                "date": "16 Jan 17",
                "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17011659129732",
                "balanceAmount": 21166,
                "category": [
                    "Transfer",
                    "Earning"
                ]
            },
            {
                "amount": 5183,
                "date": "05 Jan 17",
                "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17010550345082",
                "balanceAmount": 16473,
                "category": [
                    "Transfer",
                    "Earning"
                ]
            },
            {
                "amount": 5062,
                "date": "10 Jan 17",
                "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17011054754055",
                "balanceAmount": 13354,
                "category": [
                    "Transfer",
                    "Earning"
                ]
            },
            {
                "amount": 5009,
                "date": "28 Mar 17",
                "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES-ROHAN GANDHI-N087170010038439",
                "balanceAmount": 12521,
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
                "particular": "IB BILLPAY DR-HDFCVE-4112442XXXXXX8872",
                "balanceAmount": 27681,
                "category": [
                    "Payment"
                ]
            },
            {
                "amount": 17662,
                "date": "25 Mar 17",
                "particular": "NF2291297394804P3/DEMOOO COM",
                "balanceAmount": 4185,
                "category": [
                    "Travel"
                ]
            },
            {
                "amount": 16000,
                "date": "09 Jan 17",
                "particular": "NEFT DR-IDIB000S208-SURYA RATHI-NETBANK, MUM-N009170230731858",
                "balanceAmount": 7213,
                "category": [
                    "Transfer",
                    "Debit"
                ]
            },
            {
                "amount": 14587,
                "date": "08 Feb 17",
                "particular": "IB BILLPAY DR-HDFCVE-4112442XXXXXX8872",
                "balanceAmount": 48544,
                "category": [
                    "Payment"
                ]
            },
            {
                "amount": 14400,
                "date": "23 Jun 17",
                "particular": "ACH D- AUFINANCIERS-9001020101524623",
                "balanceAmount": 1080,
                "category": [
                    "Payment",
                    "Loan"
                ]
            },
            {
                "amount": 14400,
                "date": "23 May 17",
                "particular": "ACH D- AUFINANCIERS-LVPTU04016-170458917",
                "balanceAmount": 1814,
                "category": [
                    "Payment",
                    "Loan"
                ]
            },
            {
                "amount": 14400,
                "date": "24 Apr 17",
                "particular": "ACH D- AUFINANCIERSINDIALTD-LVPTU04016-1",
                "balanceAmount": 2730,
                "category": [
                    "Payment",
                    "Loan"
                ]
            },
            {
                "amount": 14400,
                "date": "23 Feb 17",
                "particular": "ACH D- AUFINANCIERSINDIALTD-LVPTU04016-1",
                "balanceAmount": 603,
                "category": [
                    "Payment",
                    "Loan"
                ]
            },
            {
                "amount": 14400,
                "date": "23 Jan 17",
                "particular": "ACH D- AUFINANCIERSINDIALTD-LVPTU04016-1",
                "balanceAmount": 305,
                "category": [
                    "Payment",
                    "Loan"
                ]
            },
            {
                "amount": 13300,
                "date": "08 Feb 17",
                "particular": "NEFT DR-UTIB0000007-PAWAN KUMAR-NETBANK,MUM-N039170244398826",
                "balanceAmount": 35244,
                "category": [
                    "Transfer",
                    "Debit"
                ]
            }
        ],
        "monthlyRecurringDebits": {
            "months": [
                "17/06",
                "17/05",
                "17/04",
                "17/03",
                "17/02",
                "17/01"
            ],
            "data": [
                {
                    "summary": "neft dr idib000s208 SURYA rathi netbank mum n",
                    "count": 17,
                    "amount": 102000,
                    "monthlyTransactions": {
                        "17/01": {
                            "month": "17/01",
                            "amount": 46000,
                            "count": 8,
                            "transactions": [
                                {
                                    "particular": "NEFT DR-IDIB000S208-SURYA RATHI-NETBANK, MUM-N002170226538872",
                                    "date": "02/01/17",
                                    "amount": 5000,
                                    "balanceAmount": 7828.11
                                },
                                {
                                    "particular": "NEFT DR-IDIB000S208-SURYA RATHI-NETBANK, MUM-N004170228047394",
                                    "date": "04/01/17",
                                    "amount": 3000,
                                    "balanceAmount": 10911.11
                                },
                                {
                                    "particular": "NEFT DR-IDIB000S208-SURYA RATHI-NETBANK, MUM-N009170230731858",
                                    "date": "09/01/17",
                                    "amount": 16000,
                                    "balanceAmount": 7213.07
                                },
                                {
                                    "particular": "NEFT DR-IDIB000S208-SURYA RATHI-NETBANK, MUM-N010170231151679",
                                    "date": "10/01/17",
                                    "amount": 5000,
                                    "balanceAmount": 8292.19
                                },
                                {
                                    "particular": "NEFT DR-IDIB000S208-SURYA RATHI-NETBANK, MUM-N012170232384757",
                                    "date": "12/01/17",
                                    "amount": 4000,
                                    "balanceAmount": 16081.19
                                },
                                {
                                    "particular": "NEFT DR-IDIB000S208-SURYA RATHI-NETBANK, MUM-N016170233524951",
                                    "date": "16/01/17",
                                    "amount": 5000,
                                    "balanceAmount": 10860.44
                                },
                                {
                                    "particular": "NEFT DR-IDIB000S208-SURYA RATHI-NETBANK, MUM-N017170234021814",
                                    "date": "17/01/17",
                                    "amount": 5000,
                                    "balanceAmount": 16165.68
                                },
                                {
                                    "particular": "NEFT DR-IDIB000S208-SURYA RATHI-NETBANK, MUM-N025170237139856",
                                    "date": "25/01/17",
                                    "amount": 3000,
                                    "balanceAmount": 413.17
                                }
                            ]
                        },
                        "17/02": {
                            "month": "17/02",
                            "amount": 38000,
                            "count": 5,
                            "transactions": [
                                {
                                    "particular": "NEFT DR-IDIB000S208-SURYA RATHI-NETBANK, MUM-N037170242706549",
                                    "date": "06/02/17",
                                    "amount": 8000,
                                    "balanceAmount": 748.66
                                },
                                {
                                    "particular": "NEFT DR-IDIB000S208-SURYA RATHI-NETBANK, MUM-N040170244633960",
                                    "date": "09/02/17",
                                    "amount": 9000,
                                    "balanceAmount": 27679.18
                                },
                                {
                                    "particular": "NEFT DR-IDIB000S208-SURYA RATHI-NETBANK, MUM-N047170247654360",
                                    "date": "16/02/17",
                                    "amount": 6000,
                                    "balanceAmount": 2054.79
                                },
                                {
                                    "particular": "NEFT DR-IDIB000S208-SURYA RATHI-NETBANK, MUM-N051170248779164",
                                    "date": "20/02/17",
                                    "amount": 10000,
                                    "balanceAmount": 5140.91
                                },
                                {
                                    "particular": "NEFT DR-IDIB000S208-SURYA RATHI-NETBANK, MUM-N052170249321805",
                                    "date": "21/02/17",
                                    "amount": 5000,
                                    "balanceAmount": 5508.16
                                }
                            ]
                        },
                        "17/05": {
                            "month": "17/05",
                            "amount": 8000,
                            "count": 2,
                            "transactions": [
                                {
                                    "particular": "NEFT DR-IDIB000S208-SURYA RATHI-NETBANK, MUM-N149170301039889",
                                    "date": "29/05/17",
                                    "amount": 5000,
                                    "balanceAmount": 499.98
                                },
                                {
                                    "particular": "NEFT DR-IDIB000S208-SURYA RATHI-NETBANK, MUM-N150170302195450",
                                    "date": "30/05/17",
                                    "amount": 3000,
                                    "balanceAmount": 3890.98
                                }
                            ]
                        },
                        "17/06": {
                            "month": "17/06",
                            "amount": 10000,
                            "count": 2,
                            "transactions": [
                                {
                                    "particular": "NEFT DR-IDIB000S208-SURYA RATHI-NETBANK, MUM-N167170314437615",
                                    "date": "16/06/17",
                                    "amount": 5000,
                                    "balanceAmount": 5177.23
                                },
                                {
                                    "particular": "NEFT DR-IDIB000S208-SURYA RATHI-NETBANK, MUM-N168170314791724",
                                    "date": "17/06/17",
                                    "amount": 5000,
                                    "balanceAmount": 1786.23
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "ib billpay dr hdfcve 4112442xxxxxx8872",
                    "count": 6,
                    "amount": 75668.12,
                    "monthlyTransactions": {
                        "17/01": {
                            "month": "17/01",
                            "amount": 11253.44,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "IB BILLPAY DR-HDFCVE-4112442XXXXXX8872",
                                    "date": "07/01/17",
                                    "amount": 11253.44,
                                    "balanceAmount": 3212.13
                                }
                            ]
                        },
                        "17/02": {
                            "month": "17/02",
                            "amount": 14587.14,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "IB BILLPAY DR-HDFCVE-4112442XXXXXX8872",
                                    "date": "08/02/17",
                                    "amount": 14587.14,
                                    "balanceAmount": 48544.18
                                }
                            ]
                        },
                        "17/03": {
                            "month": "17/03",
                            "amount": 26103.81,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "IB BILLPAY DR-HDFCVE-4112442XXXXXX8872",
                                    "date": "08/03/17",
                                    "amount": 26103.81,
                                    "balanceAmount": 27681.09
                                }
                            ]
                        },
                        "17/04": {
                            "month": "17/04",
                            "amount": 18112.690000000002,
                            "count": 2,
                            "transactions": [
                                {
                                    "particular": "IB BILLPAY DR-HDFCVE-4112442XXXXXX8872",
                                    "date": "07/04/17",
                                    "amount": 8638.61,
                                    "balanceAmount": 1266.19
                                },
                                {
                                    "particular": "IB BILLPAY DR-HDFCVE-4112442XXXXXX8872",
                                    "date": "20/04/17",
                                    "amount": 9474.08,
                                    "balanceAmount": 12639.46
                                }
                            ]
                        },
                        "17/06": {
                            "month": "17/06",
                            "amount": 5611.04,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "IB BILLPAY DR-HDFCVE-4112442XXXXXX8872",
                                    "date": "07/06/17",
                                    "amount": 5611.04,
                                    "balanceAmount": 1819.18
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "ach d aufinanciersindialtd lvptu04016 1",
                    "count": 3,
                    "amount": 43200,
                    "monthlyTransactions": {
                        "17/01": {
                            "month": "17/01",
                            "amount": 14400,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "ACH D- AUFINANCIERSINDIALTD-LVPTU04016-1",
                                    "date": "23/01/17",
                                    "amount": 14400,
                                    "balanceAmount": 305.17
                                }
                            ]
                        },
                        "17/02": {
                            "month": "17/02",
                            "amount": 14400,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "ACH D- AUFINANCIERSINDIALTD-LVPTU04016-1",
                                    "date": "23/02/17",
                                    "amount": 14400,
                                    "balanceAmount": 602.9
                                }
                            ]
                        },
                        "17/04": {
                            "month": "17/04",
                            "amount": 14400,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "ACH D- AUFINANCIERSINDIALTD-LVPTU04016-1",
                                    "date": "24/04/17",
                                    "amount": 14400,
                                    "balanceAmount": 2730.46
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "eaw 436303xxxxxx9999 becn1262 faridabad",
                    "count": 7,
                    "amount": 37000,
                    "monthlyTransactions": {
                        "17/01": {
                            "month": "17/01",
                            "amount": 5000,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "EAW-436303XXXXXX9999-BECN1262-faridabad",
                                    "date": "19/01/17",
                                    "amount": 5000,
                                    "balanceAmount": 4212.68
                                }
                            ]
                        },
                        "17/02": {
                            "month": "17/02",
                            "amount": 5000,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "EAW-436303XXXXXX9999-BECN1262-faridabad",
                                    "date": "10/02/17",
                                    "amount": 5000,
                                    "balanceAmount": 18378.18
                                }
                            ]
                        },
                        "17/04": {
                            "month": "17/04",
                            "amount": 25000,
                            "count": 4,
                            "transactions": [
                                {
                                    "particular": "EAW-436303XXXXXX9999-BECN1262-faridabad",
                                    "date": "27/04/17",
                                    "amount": 2000,
                                    "balanceAmount": 2383.46
                                },
                                {
                                    "particular": "EAW-436303XXXXXX9999-BECN1262-faridabad",
                                    "date": "28/04/17",
                                    "amount": 10000,
                                    "balanceAmount": 15934.46
                                },
                                {
                                    "particular": "EAW-436303XXXXXX9999-BECN1262-faridabad",
                                    "date": "28/04/17",
                                    "amount": 10000,
                                    "balanceAmount": 5934.46
                                },
                                {
                                    "particular": "EAW-436303XXXXXX9999-BECN1262-faridabad",
                                    "date": "28/04/17",
                                    "amount": 3000,
                                    "balanceAmount": 2934.46
                                }
                            ]
                        },
                        "17/06": {
                            "month": "17/06",
                            "amount": 2000,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "EAW-436303XXXXXX9999-BECN1262-faridabad",
                                    "date": "08/06/17",
                                    "amount": 2000,
                                    "balanceAmount": 1327.18
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "finemi bf 1189499",
                    "count": 11,
                    "amount": 36170,
                    "monthlyTransactions": {
                        "17/01": {
                            "month": "17/01",
                            "amount": 4500,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "BAJAFINEMI-BF-1189499-93735",
                                    "date": "05/01/17",
                                    "amount": 4500,
                                    "balanceAmount": 6411.11
                                }
                            ]
                        },
                        "17/02": {
                            "month": "17/02",
                            "amount": 6334,
                            "count": 2,
                            "transactions": [
                                {
                                    "particular": "BAJAFINEMI-BF-1189499-245524",
                                    "date": "02/02/17",
                                    "amount": 1834,
                                    "balanceAmount": 7575.66
                                },
                                {
                                    "particular": "BAJAFINEMI-BF-1189499-213821",
                                    "date": "06/02/17",
                                    "amount": 4500,
                                    "balanceAmount": 8748.66
                                }
                            ]
                        },
                        "17/03": {
                            "month": "17/03",
                            "amount": 6334,
                            "count": 2,
                            "transactions": [
                                {
                                    "particular": "BAJAFINEMI-BF-1189499-55452",
                                    "date": "02/03/17",
                                    "amount": 1834,
                                    "balanceAmount": 893.4
                                },
                                {
                                    "particular": "BAJAJFINEMI-BF-1189499-7230",
                                    "date": "07/03/17",
                                    "amount": 4500,
                                    "balanceAmount": 1784.9
                                }
                            ]
                        },
                        "17/04": {
                            "month": "17/04",
                            "amount": 6334,
                            "count": 2,
                            "transactions": [
                                {
                                    "particular": "BAJAJ FINEMI-BF-1189499-51163",
                                    "date": "03/04/17",
                                    "amount": 1834,
                                    "balanceAmount": 4091.53
                                },
                                {
                                    "particular": "BAJAJ FINEMI-BF-1189499-43484",
                                    "date": "05/04/17",
                                    "amount": 4500,
                                    "balanceAmount": 8198.8
                                }
                            ]
                        },
                        "17/05": {
                            "month": "17/05",
                            "amount": 6334,
                            "count": 2,
                            "transactions": [
                                {
                                    "particular": "BAJAJ FINEMI-BF-1189499-49939",
                                    "date": "02/05/17",
                                    "amount": 1834,
                                    "balanceAmount": 4760.96
                                },
                                {
                                    "particular": "BAJAJ FINEMI-BF-1189499-35828",
                                    "date": "05/05/17",
                                    "amount": 4500,
                                    "balanceAmount": 5973.46
                                }
                            ]
                        },
                        "17/06": {
                            "month": "17/06",
                            "amount": 6334,
                            "count": 2,
                            "transactions": [
                                {
                                    "particular": "BAJAJ FINEMI-BF-1189499-216580",
                                    "date": "02/06/17",
                                    "amount": 1834,
                                    "balanceAmount": 1783.22
                                },
                                {
                                    "particular": "BAJAJ FINEMI-BF-1189499-80864",
                                    "date": "05/06/17",
                                    "amount": 4500,
                                    "balanceAmount": 755.22
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "nwd 436303xxxxxx9999",
                    "count": 6,
                    "amount": 29000,
                    "monthlyTransactions": {
                        "17/01": {
                            "month": "17/01",
                            "amount": 3000,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "NWD-436303XXXXXX9999-N2895001-faridabad",
                                    "date": "27/01/17",
                                    "amount": 3000,
                                    "balanceAmount": 584.17
                                }
                            ]
                        },
                        "17/02": {
                            "month": "17/02",
                            "amount": 4000,
                            "count": 2,
                            "transactions": [
                                {
                                    "particular": "NWD-436303XXXXXX9999-S1CN3496-faridabad",
                                    "date": "02/02/17",
                                    "amount": 2000,
                                    "balanceAmount": 5575.66
                                },
                                {
                                    "particular": "NWD-436303XXXXXX9999-S1CN5684-faridabad",
                                    "date": "27/02/17",
                                    "amount": 2000,
                                    "balanceAmount": 422.4
                                }
                            ]
                        },
                        "17/03": {
                            "month": "17/03",
                            "amount": 20000,
                            "count": 2,
                            "transactions": [
                                {
                                    "particular": "NWD-436303XXXXXX9999-STCH9855-faridabad",
                                    "date": "10/03/17",
                                    "amount": 10000,
                                    "balanceAmount": 19212.59
                                },
                                {
                                    "particular": "NWD-436303XXXXXX9999-STCH9855-faridabad",
                                    "date": "10/03/17",
                                    "amount": 10000,
                                    "balanceAmount": 9212.59
                                }
                            ]
                        },
                        "17/05": {
                            "month": "17/05",
                            "amount": 2000,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "NWD-436303XXXXXX9999-S1CN3496-faridabad",
                                    "date": "20/05/17",
                                    "amount": 2000,
                                    "balanceAmount": 3549.48
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "SURYA rathi idib xxxxxx2713 load",
                    "count": 4,
                    "amount": 29000,
                    "monthlyTransactions": {
                        "17/02": {
                            "month": "17/02",
                            "amount": 25000,
                            "count": 3,
                            "transactions": [
                                {
                                    "particular": "IMPS-703211108906-SURYA RATHI-IDIB-XXXXXX2713-LOAD",
                                    "date": "01/02/17",
                                    "amount": 10000,
                                    "balanceAmount": 6180.66
                                },
                                {
                                    "particular": "IMPS-703312102642-SURYA RATHI-IDIB-XXXXXX2713-LOAD",
                                    "date": "02/02/17",
                                    "amount": 5000,
                                    "balanceAmount": 2575.66
                                },
                                {
                                    "particular": "IMPS-704612304375-SURYA RATHI-IDIB-XXXXXX2713-LOAD",
                                    "date": "15/02/17",
                                    "amount": 10000,
                                    "balanceAmount": 9326.79
                                }
                            ]
                        },
                        "17/03": {
                            "month": "17/03",
                            "amount": 4000,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "IMPS-7075111919-SURYA RATHI-IDIB-XXXXXX2713-LOAD",
                                    "date": "16/03/17",
                                    "amount": 4000,
                                    "balanceAmount": 6116.28
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "ach d aufinanciers",
                    "count": 2,
                    "amount": 28800,
                    "monthlyTransactions": {
                        "17/05": {
                            "month": "17/05",
                            "amount": 14400,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "ACH D- AUFINANCIERS-LVPTU04016-170458917",
                                    "date": "23/05/17",
                                    "amount": 14400,
                                    "balanceAmount": 1813.98
                                }
                            ]
                        },
                        "17/06": {
                            "month": "17/06",
                            "amount": 14400,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "ACH D- AUFINANCIERS-9001020101524623",
                                    "date": "23/06/17",
                                    "amount": 14400,
                                    "balanceAmount": 1080.2
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "DEMOOO com",
                    "count": 2,
                    "amount": 21768,
                    "monthlyTransactions": {
                        "17/03": {
                            "month": "17/03",
                            "amount": 17662,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "NF2291297394804P3/DEMOOO COM",
                                    "date": "25/03/17",
                                    "amount": 17662,
                                    "balanceAmount": 4185.03
                                }
                            ]
                        },
                        "17/05": {
                            "month": "17/05",
                            "amount": 4106,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "NF22911100534896P01/DEMOOO COM",
                                    "date": "06/05/17",
                                    "amount": 4106,
                                    "balanceAmount": 3815.21
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "irctc_new",
                    "count": 40,
                    "amount": 19840,
                    "monthlyTransactions": {
                        "17/01": {
                            "month": "17/01",
                            "amount": 4331,
                            "count": 8,
                            "transactions": [
                                {
                                    "particular": "100000709755560/IRCTC_NEW",
                                    "date": "12/01/17",
                                    "amount": 620,
                                    "balanceAmount": 20594.19
                                },
                                {
                                    "particular": "100000709755560/IRCTC_NEW",
                                    "date": "12/01/17",
                                    "amount": 11.5,
                                    "balanceAmount": 20582.69
                                },
                                {
                                    "particular": "100000709796984/IRCTC_NEW",
                                    "date": "12/01/17",
                                    "amount": 490,
                                    "balanceAmount": 20092.69
                                },
                                {
                                    "particular": "100000709796984/IRCTC_NEW",
                                    "date": "12/01/17",
                                    "amount": 11.5,
                                    "balanceAmount": 20081.19
                                },
                                {
                                    "particular": "100000720121379/IRCTC_NEW",
                                    "date": "20/01/17",
                                    "amount": 2420,
                                    "balanceAmount": 6948.55
                                },
                                {
                                    "particular": "100000720121379/IRCTC_NEW",
                                    "date": "20/01/17",
                                    "amount": 11.5,
                                    "balanceAmount": 6937.05
                                },
                                {
                                    "particular": "100000729819722/IRCTC_NEW",
                                    "date": "31/01/17",
                                    "amount": 755,
                                    "balanceAmount": 9193.16
                                },
                                {
                                    "particular": "100000729819722/IRCTC_NEW",
                                    "date": "31/01/17",
                                    "amount": 11.5,
                                    "balanceAmount": 9181.66
                                }
                            ]
                        },
                        "17/02": {
                            "month": "17/02",
                            "amount": 4094.5,
                            "count": 6,
                            "transactions": [
                                {
                                    "particular": "100000749518828/IRCTC_NEW",
                                    "date": "19/02/17",
                                    "amount": 725,
                                    "balanceAmount": 13152.41
                                },
                                {
                                    "particular": "100000749518828/IRCTC_NEW",
                                    "date": "19/02/17",
                                    "amount": 11.5,
                                    "balanceAmount": 13140.91
                                },
                                {
                                    "particular": "100000752067007/IRCTC_NEW",
                                    "date": "21/02/17",
                                    "amount": 2085,
                                    "balanceAmount": 3423.16
                                },
                                {
                                    "particular": "100000752067007/IRCTC_NEW",
                                    "date": "21/02/17",
                                    "amount": 11.5,
                                    "balanceAmount": 3411.66
                                },
                                {
                                    "particular": "100000755864005/IRCTC_NEW",
                                    "date": "24/02/17",
                                    "amount": 1250,
                                    "balanceAmount": 1683.9
                                },
                                {
                                    "particular": "100000755864005/IRCTC_NEW",
                                    "date": "24/02/17",
                                    "amount": 11.5,
                                    "balanceAmount": 1672.4
                                }
                            ]
                        },
                        "17/03": {
                            "month": "17/03",
                            "amount": 1403,
                            "count": 4,
                            "transactions": [
                                {
                                    "particular": "100000764874585/IRCTC_NEW",
                                    "date": "05/03/17",
                                    "amount": 590,
                                    "balanceAmount": 4001.4
                                },
                                {
                                    "particular": "100000764874585/IRCTC_NEW",
                                    "date": "05/03/17",
                                    "amount": 11.5,
                                    "balanceAmount": 3989.9
                                },
                                {
                                    "particular": "100000776202346/IRCTC_NEW",
                                    "date": "15/03/17",
                                    "amount": 790,
                                    "balanceAmount": 9671.59
                                },
                                {
                                    "particular": "100000776202346/IRCTC_NEW",
                                    "date": "15/03/17",
                                    "amount": 11.5,
                                    "balanceAmount": 9660.09
                                }
                            ]
                        },
                        "17/04": {
                            "month": "17/04",
                            "amount": 1923,
                            "count": 4,
                            "transactions": [
                                {
                                    "particular": "100000809967866/IRCTC_NEW",
                                    "date": "17/04/17",
                                    "amount": 1080,
                                    "balanceAmount": 16722.54
                                },
                                {
                                    "particular": "100000809967866/IRCTC_NEW",
                                    "date": "17/04/17",
                                    "amount": 11.5,
                                    "balanceAmount": 16711.04
                                },
                                {
                                    "particular": "100000823590011/IRCTC_NEW",
                                    "date": "29/04/17",
                                    "amount": 820,
                                    "balanceAmount": 3824.46
                                },
                                {
                                    "particular": "100000823590011/IRCTC_NEW",
                                    "date": "29/04/17",
                                    "amount": 11.5,
                                    "balanceAmount": 3812.96
                                }
                            ]
                        },
                        "17/05": {
                            "month": "17/05",
                            "amount": 5502.5,
                            "count": 10,
                            "transactions": [
                                {
                                    "particular": "100000836234812/IRCTC_NEW",
                                    "date": "11/05/17",
                                    "amount": 805,
                                    "balanceAmount": 2745.98
                                },
                                {
                                    "particular": "100000836234812/IRCTC_NEW",
                                    "date": "11/05/17",
                                    "amount": 11.5,
                                    "balanceAmount": 2734.48
                                },
                                {
                                    "particular": "100000843023118/IRCTC_NEW",
                                    "date": "17/05/17",
                                    "amount": 805,
                                    "balanceAmount": 4057.48
                                },
                                {
                                    "particular": "100000843023118/IRCTC_NEW",
                                    "date": "17/05/17",
                                    "amount": 11.5,
                                    "balanceAmount": 4045.98
                                },
                                {
                                    "particular": "100000845851579/IRCTC_NEW",
                                    "date": "19/05/17",
                                    "amount": 2215,
                                    "balanceAmount": 2913.98
                                },
                                {
                                    "particular": "100000845851579/IRCTC_NEW",
                                    "date": "19/05/17",
                                    "amount": 11.5,
                                    "balanceAmount": 2902.48
                                },
                                {
                                    "particular": "100000848921380/IRCTC_NEW",
                                    "date": "22/05/17",
                                    "amount": 830,
                                    "balanceAmount": 2719.48
                                },
                                {
                                    "particular": "100000848921380/IRCTC_NEW",
                                    "date": "22/05/17",
                                    "amount": 11.5,
                                    "balanceAmount": 2707.98
                                },
                                {
                                    "particular": "100000849785885/IRCTC_NEW",
                                    "date": "23/05/17",
                                    "amount": 790,
                                    "balanceAmount": 15261.98
                                },
                                {
                                    "particular": "100000849785885/IRCTC_NEW",
                                    "date": "23/05/17",
                                    "amount": 11.5,
                                    "balanceAmount": 15250.48
                                }
                            ]
                        },
                        "17/06": {
                            "month": "17/06",
                            "amount": 2586,
                            "count": 8,
                            "transactions": [
                                {
                                    "particular": "100000878441519/IRCTC_NEW",
                                    "date": "17/06/17",
                                    "amount": 1100,
                                    "balanceAmount": 686.23
                                },
                                {
                                    "particular": "100000878441519/IRCTC_NEW",
                                    "date": "17/06/17",
                                    "amount": 11.5,
                                    "balanceAmount": 674.73
                                },
                                {
                                    "particular": "100000879294446/IRCTC_NEW",
                                    "date": "18/06/17",
                                    "amount": 500,
                                    "balanceAmount": 2174.73
                                },
                                {
                                    "particular": "100000879294446/IRCTC_NEW",
                                    "date": "18/06/17",
                                    "amount": 11.5,
                                    "balanceAmount": 2163.23
                                },
                                {
                                    "particular": "100000880077617/IRCTC_NEW",
                                    "date": "19/06/17",
                                    "amount": 470,
                                    "balanceAmount": 1693.23
                                },
                                {
                                    "particular": "100000880077617/IRCTC_NEW",
                                    "date": "19/06/17",
                                    "amount": 11.5,
                                    "balanceAmount": 1681.73
                                },
                                {
                                    "particular": "100000880120515/IRCTC_NEW",
                                    "date": "19/06/17",
                                    "amount": 470,
                                    "balanceAmount": 1211.73
                                },
                                {
                                    "particular": "100000880120515/IRCTC_NEW",
                                    "date": "19/06/17",
                                    "amount": 11.5,
                                    "balanceAmount": 1200.23
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "pos 436303xxxxxx9999 paytm mobile sol pos debit",
                    "count": 6,
                    "amount": 16900,
                    "monthlyTransactions": {
                        "17/01": {
                            "month": "17/01",
                            "amount": 3000,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "POS 436303XXXXXX9999 PAYTM MOBILE SOL POS DEBIT",
                                    "date": "03/01/17",
                                    "amount": 3000,
                                    "balanceAmount": 13911.11
                                }
                            ]
                        },
                        "17/03": {
                            "month": "17/03",
                            "amount": 10000,
                            "count": 2,
                            "transactions": [
                                {
                                    "particular": "POS 436303XXXXXX9999 PAYTM MOBILE SOL POS DEBIT",
                                    "date": "31/03/17",
                                    "amount": 5000,
                                    "balanceAmount": 9082.53
                                },
                                {
                                    "particular": "POS 436303XXXXXX9999 PAYTM MOBILE SOL POS DEBIT",
                                    "date": "31/03/17",
                                    "amount": 5000,
                                    "balanceAmount": 4082.53
                                }
                            ]
                        },
                        "17/04": {
                            "month": "17/04",
                            "amount": 2000,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "POS 436303XXXXXX9999 PAYTM MOBILE SOL POS DEBIT",
                                    "date": "04/04/17",
                                    "amount": 2000,
                                    "balanceAmount": 12056.53
                                }
                            ]
                        },
                        "17/05": {
                            "month": "17/05",
                            "amount": 1300,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "POS 436303XXXXXX9999 PAYTM MOBILE SOL POS DEBIT",
                                    "date": "31/05/17",
                                    "amount": 1300,
                                    "balanceAmount": 3427.98
                                }
                            ]
                        },
                        "17/06": {
                            "month": "17/06",
                            "amount": 600,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "POS 436303XXXXXX9999 PAYTM MOBILE SOL POS DEBIT",
                                    "date": "19/06/17",
                                    "amount": 600,
                                    "balanceAmount": 2046.23
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "pos 436303xxxxxx9999 paytm app pos debit",
                    "count": 4,
                    "amount": 10500,
                    "monthlyTransactions": {
                        "17/02": {
                            "month": "17/02",
                            "amount": 10500,
                            "count": 4,
                            "transactions": [
                                {
                                    "particular": "POS 436303XXXXXX9999 PAYTM APP POS DEBIT",
                                    "date": "09/02/17",
                                    "amount": 5000,
                                    "balanceAmount": 23378.18
                                },
                                {
                                    "particular": "POS 436303XXXXXX9999 PAYTM APP POS DEBIT",
                                    "date": "11/02/17",
                                    "amount": 2500,
                                    "balanceAmount": 14296.18
                                },
                                {
                                    "particular": "POS 436303XXXXXX9999 PAYTM APP POS DEBIT",
                                    "date": "15/02/17",
                                    "amount": 1000,
                                    "balanceAmount": 9202.79
                                },
                                {
                                    "particular": "POS 436303XXXXXX9999 PAYTM APP POS DEBIT",
                                    "date": "18/02/17",
                                    "amount": 2000,
                                    "balanceAmount": 13877.41
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "pos 436303xxxxxx9999 one97 communicat pos debit",
                    "count": 3,
                    "amount": 10000,
                    "monthlyTransactions": {
                        "17/01": {
                            "month": "17/01",
                            "amount": 7000,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "POS 436303XXXXXX9999 ONE97 COMMUNICAT POS DEBIT",
                                    "date": "17/01/17",
                                    "amount": 7000,
                                    "balanceAmount": 8612.68
                                }
                            ]
                        },
                        "17/05": {
                            "month": "17/05",
                            "amount": 3000,
                            "count": 2,
                            "transactions": [
                                {
                                    "particular": "POS 436303XXXXXX9999 ONE97 COMMUNICAT POS DEBIT",
                                    "date": "03/05/17",
                                    "amount": 1000,
                                    "balanceAmount": 8676.46
                                },
                                {
                                    "particular": "POS 436303XXXXXX9999 ONE97 COMMUNICAT POS DEBIT",
                                    "date": "26/05/17",
                                    "amount": 2000,
                                    "balanceAmount": 5499.98
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "chq paid micr cts no sd adarsh vidyalaya",
                    "count": 2,
                    "amount": 9400,
                    "monthlyTransactions": {
                        "17/01": {
                            "month": "17/01",
                            "amount": 5640,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "CHQ PAID-MICR CTS-NO-SD ADARSH VIDYALAYA",
                                    "date": "21/01/17",
                                    "amount": 5640,
                                    "balanceAmount": 1298.05
                                }
                            ]
                        },
                        "17/05": {
                            "month": "17/05",
                            "amount": 3760,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "CHQ PAID-MICR CTS-NO-SD ADARSH VIDYALAYA",
                                    "date": "19/05/17",
                                    "amount": 3760,
                                    "balanceAmount": 5128.98
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "TELE communication andb xxxxxxxxxxx0520 per",
                    "count": 2,
                    "amount": 9300,
                    "monthlyTransactions": {
                        "17/05": {
                            "month": "17/05",
                            "amount": 9300,
                            "count": 2,
                            "transactions": [
                                {
                                    "particular": "IMPS-712912173445-TELE COMMUNICATION-ANDB-XXXXXXXXXXX0520-PEROSNAL",
                                    "date": "09/05/17",
                                    "amount": 6000,
                                    "balanceAmount": 712.98
                                },
                                {
                                    "particular": "IMPS-712916138399-TELE COMMUNICATION-ANDB-XXXXXXXXXXX0520-PERSONAL",
                                    "date": "09/05/17",
                                    "amount": 3300,
                                    "balanceAmount": 1626.98
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "neft dr stbp0001117 vidya devi netbank mum n",
                    "count": 3,
                    "amount": 5500,
                    "monthlyTransactions": {
                        "17/01": {
                            "month": "17/01",
                            "amount": 2500,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "NEFT DR-STBP0001117-VIDYA DEVI-NETBANK,MUM-N025170237107852",
                                    "date": "25/01/17",
                                    "amount": 2500,
                                    "balanceAmount": 2263.17
                                }
                            ]
                        },
                        "17/02": {
                            "month": "17/02",
                            "amount": 1000,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "NEFT DR-STBP0001117-VIDYA DEVI-NETBANK,MUM-N035170242040146",
                                    "date": "04/02/17",
                                    "amount": 1000,
                                    "balanceAmount": 9429.66
                                }
                            ]
                        },
                        "17/06": {
                            "month": "17/06",
                            "amount": 2000,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "NEFT DR-STBP0001117-VIDYA DEVI-NETBANK,MUM-N166170313506800",
                                    "date": "15/06/17",
                                    "amount": 2000,
                                    "balanceAmount": 6071.23
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "PAYUDEMOCOM",
                    "count": 15,
                    "amount": 5168,
                    "monthlyTransactions": {
                        "17/03": {
                            "month": "17/03",
                            "amount": 2896,
                            "count": 5,
                            "transactions": [
                                {
                                    "particular": "6039491118/PAYUDEMOCOM",
                                    "date": "05/03/17",
                                    "amount": 100,
                                    "balanceAmount": 3889.9
                                },
                                {
                                    "particular": "6050512581/PAYUDEMOCOM",
                                    "date": "18/03/17",
                                    "amount": 599,
                                    "balanceAmount": 8325.28
                                },
                                {
                                    "particular": "6053647722/PAYUDEMOCOM",
                                    "date": "21/03/17",
                                    "amount": 999,
                                    "balanceAmount": 9861.28
                                },
                                {
                                    "particular": "6054447191/PAYUDEMOCOM",
                                    "date": "22/03/17",
                                    "amount": 599,
                                    "balanceAmount": 14368.53
                                },
                                {
                                    "particular": "6062339690/PAYUDEMOCOM",
                                    "date": "29/03/17",
                                    "amount": 599,
                                    "balanceAmount": 12884.03
                                }
                            ]
                        },
                        "17/04": {
                            "month": "17/04",
                            "amount": 1400,
                            "count": 5,
                            "transactions": [
                                {
                                    "particular": "6079185444/PAYUDEMOCOM",
                                    "date": "07/04/17",
                                    "amount": 200,
                                    "balanceAmount": 8668.8
                                },
                                {
                                    "particular": "6085805830/PAYUDEMOCOM",
                                    "date": "10/04/17",
                                    "amount": 300,
                                    "balanceAmount": 318.97
                                },
                                {
                                    "particular": "6089601712/PAYUDEMOCOM",
                                    "date": "12/04/17",
                                    "amount": 400,
                                    "balanceAmount": 10128.54
                                },
                                {
                                    "particular": "6091924718/PAYUDEMOCOM",
                                    "date": "14/04/17",
                                    "amount": 200,
                                    "balanceAmount": 14165.54
                                },
                                {
                                    "particular": "6121693326/PAYUDEMOCOM",
                                    "date": "29/04/17",
                                    "amount": 300,
                                    "balanceAmount": 4094.96
                                }
                            ]
                        },
                        "17/05": {
                            "month": "17/05",
                            "amount": 672,
                            "count": 4,
                            "transactions": [
                                {
                                    "particular": "6135370620/PAYUDEMOCOM",
                                    "date": "06/05/17",
                                    "amount": 72,
                                    "balanceAmount": 7139.21
                                },
                                {
                                    "particular": "6138910074/PAYUDEMOCOM",
                                    "date": "08/05/17",
                                    "amount": 200,
                                    "balanceAmount": 5399.19
                                },
                                {
                                    "particular": "6156317854/PAYUDEMOCOM",
                                    "date": "16/05/17",
                                    "amount": 200,
                                    "balanceAmount": 6862.48
                                },
                                {
                                    "particular": "6164860348/PAYUDEMOCOM",
                                    "date": "20/05/17",
                                    "amount": 200,
                                    "balanceAmount": 3590.48
                                }
                            ]
                        },
                        "17/06": {
                            "month": "17/06",
                            "amount": 200,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "6212894082/PAYUDEMOCOM",
                                    "date": "13/06/17",
                                    "amount": 200,
                                    "balanceAmount": 4423.23
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "pos 436303xxxxxx9999 nextraworld",
                    "count": 4,
                    "amount": 4592,
                    "monthlyTransactions": {
                        "17/01": {
                            "month": "17/01",
                            "amount": 1148,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "POS 436303XXXXXX9999 NEXTRAWORLD POS DEBIT",
                                    "date": "16/01/17",
                                    "amount": 1148,
                                    "balanceAmount": 15860.44
                                }
                            ]
                        },
                        "17/02": {
                            "month": "17/02",
                            "amount": 1148,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "POS 436303XXXXXX9999 NEXTRAWORLD_PAYT POS DEBIT",
                                    "date": "16/02/17",
                                    "amount": 1148,
                                    "balanceAmount": 8054.79
                                }
                            ]
                        },
                        "17/03": {
                            "month": "17/03",
                            "amount": 1148,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "POS 436303XXXXXX9999 NEXTRAWORLD POS DEBIT",
                                    "date": "07/03/17",
                                    "amount": 1148,
                                    "balanceAmount": 4984.9
                                }
                            ]
                        },
                        "17/05": {
                            "month": "17/05",
                            "amount": 1148,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "POS 436303XXXXXX9999 NEXTRAWORLD_PAYT POS DEBIT",
                                    "date": "29/05/17",
                                    "amount": 1148,
                                    "balanceAmount": 6890.98
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "pos 436303xxxxxx9999 instakart pos debit",
                    "count": 3,
                    "amount": 2861,
                    "monthlyTransactions": {
                        "17/01": {
                            "month": "17/01",
                            "amount": 553,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "POS 436303XXXXXX9999 INSTAKART. POS DEBIT",
                                    "date": "17/01/17",
                                    "amount": 553,
                                    "balanceAmount": 15612.68
                                }
                            ]
                        },
                        "17/04": {
                            "month": "17/04",
                            "amount": 2308,
                            "count": 2,
                            "transactions": [
                                {
                                    "particular": "POS 436303XXXXXX9999 INSTAKART. POS DEBIT",
                                    "date": "01/04/17",
                                    "amount": 531,
                                    "balanceAmount": 5925.53
                                },
                                {
                                    "particular": "POS 436303XXXXXX9999 INSTAKART. POS DEBIT",
                                    "date": "17/04/17",
                                    "amount": 1777,
                                    "balanceAmount": 14934.04
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "pos 436303xxxxxx9999 dcsiideacell pos debit",
                    "count": 4,
                    "amount": 2585.88,
                    "monthlyTransactions": {
                        "17/03": {
                            "month": "17/03",
                            "amount": 695.5,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "POS 436303XXXXXX9999 DCSIIDEACELL POS DEBIT",
                                    "date": "09/03/17",
                                    "amount": 695.5,
                                    "balanceAmount": 27629.59
                                }
                            ]
                        },
                        "17/04": {
                            "month": "17/04",
                            "amount": 699.22,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "POS 436303XXXXXX9999 DCSIIDEACELL POS DEBIT",
                                    "date": "10/04/17",
                                    "amount": 699.22,
                                    "balanceAmount": 618.97
                                }
                            ]
                        },
                        "17/05": {
                            "month": "17/05",
                            "amount": 604.21,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "POS 436303XXXXXX9999 DCSIIDEACELL POS DEBIT",
                                    "date": "09/05/17",
                                    "amount": 604.21,
                                    "balanceAmount": 7860.98
                                }
                            ]
                        },
                        "17/06": {
                            "month": "17/06",
                            "amount": 586.95,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "POS 436303XXXXXX9999 DCSIIDEACELL POS DEBIT",
                                    "date": "09/06/17",
                                    "amount": 586.95,
                                    "balanceAmount": 740.23
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "pos 436303xxxxxx9999",
                    "count": 3,
                    "amount": 2317,
                    "monthlyTransactions": {
                        "17/01": {
                            "month": "17/01",
                            "amount": 500,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "POS 436303XXXXXX9999 BP 38 POS DEBIT",
                                    "date": "19/01/17",
                                    "amount": 500,
                                    "balanceAmount": 9878.68
                                }
                            ]
                        },
                        "17/02": {
                            "month": "17/02",
                            "amount": 1600,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "POS 436303XXXXXX9999 PAYTM POS DEBIT",
                                    "date": "28/02/17",
                                    "amount": 1600,
                                    "balanceAmount": 51.4
                                }
                            ]
                        },
                        "17/04": {
                            "month": "17/04",
                            "amount": 217,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "POS 436303XXXXXX9999 HCG,. POS DEBIT",
                                    "date": "18/04/17",
                                    "amount": 217,
                                    "balanceAmount": 6482.04
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "ccapaytmcom",
                    "count": 2,
                    "amount": 2296,
                    "monthlyTransactions": {
                        "17/04": {
                            "month": "17/04",
                            "amount": 1148,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "106209842001/CCAPAYTMCOM",
                                    "date": "09/04/17",
                                    "amount": 1148,
                                    "balanceAmount": 1318.19
                                }
                            ]
                        },
                        "17/05": {
                            "month": "17/05",
                            "amount": 1148,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "106223166638/CCAPAYTMCOM",
                                    "date": "09/05/17",
                                    "amount": 1148,
                                    "balanceAmount": 6712.98
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "techbookmyshow",
                    "count": 2,
                    "amount": 1216.02,
                    "monthlyTransactions": {
                        "17/05": {
                            "month": "17/05",
                            "amount": 1216.02,
                            "count": 2,
                            "transactions": [
                                {
                                    "particular": "325609046/TECHBOOKMYSHOW",
                                    "date": "07/05/17",
                                    "amount": 687.12,
                                    "balanceAmount": 6128.09
                                },
                                {
                                    "particular": "325878499/TECHBOOKMYSHOW",
                                    "date": "08/05/17",
                                    "amount": 528.9,
                                    "balanceAmount": 5599.19
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "neft chgs incl st cess",
                    "count": 21,
                    "amount": 69.10000000000001,
                    "monthlyTransactions": {
                        "17/01": {
                            "month": "17/01",
                            "amount": 31.669999999999995,
                            "count": 9,
                            "transactions": [
                                {
                                    "particular": "NEFT CHGS INCL ST & CESS 311216",
                                    "date": "07/01/17",
                                    "amount": 2.88,
                                    "balanceAmount": 9509.23
                                },
                                {
                                    "particular": "NEFT CHGS INCL ST & CESS 020117",
                                    "date": "09/01/17",
                                    "amount": 2.88,
                                    "balanceAmount": 3213.07
                                },
                                {
                                    "particular": "NEFT CHGS INCL ST & CESS 040117",
                                    "date": "09/01/17",
                                    "amount": 2.88,
                                    "balanceAmount": 7210.19
                                },
                                {
                                    "particular": "NEFT CHGS INCL ST & CESS 090117",
                                    "date": "13/01/17",
                                    "amount": 5.75,
                                    "balanceAmount": 17196.44
                                },
                                {
                                    "particular": "NEFT CHGS INCL ST & CESS 100117",
                                    "date": "16/01/17",
                                    "amount": 2.88,
                                    "balanceAmount": 10857.56
                                },
                                {
                                    "particular": "NEFT CHGS INCL ST & CESS 120117",
                                    "date": "16/01/17",
                                    "amount": 2.88,
                                    "balanceAmount": 10854.68
                                },
                                {
                                    "particular": "NEFT CHGS INCL ST & CESS 160117",
                                    "date": "20/01/17",
                                    "amount": 2.88,
                                    "balanceAmount": 7991.8
                                },
                                {
                                    "particular": "NEFT CHGS INCL ST & CESS 170117",
                                    "date": "23/01/17",
                                    "amount": 2.88,
                                    "balanceAmount": 14705.17
                                },
                                {
                                    "particular": "NEFT CHGS INCL ST & CESS 250117",
                                    "date": "30/01/17",
                                    "amount": 5.76,
                                    "balanceAmount": 4034.16
                                }
                            ]
                        },
                        "17/02": {
                            "month": "17/02",
                            "amount": 23.029999999999998,
                            "count": 7,
                            "transactions": [
                                {
                                    "particular": "NEFT CHGS INCL ST & CESS 040217",
                                    "date": "13/02/17",
                                    "amount": 2.88,
                                    "balanceAmount": 14293.3
                                },
                                {
                                    "particular": "NEFT CHGS INCL ST & CESS 060217",
                                    "date": "13/02/17",
                                    "amount": 2.88,
                                    "balanceAmount": 14290.42
                                },
                                {
                                    "particular": "NEFT CHGS INCL ST & CESS 080217",
                                    "date": "13/02/17",
                                    "amount": 5.75,
                                    "balanceAmount": 14284.67
                                },
                                {
                                    "particular": "NEFT CHGS INCL ST & CESS 090217",
                                    "date": "13/02/17",
                                    "amount": 2.88,
                                    "balanceAmount": 14281.79
                                },
                                {
                                    "particular": "NEFT CHGS INCL ST & CESS 160217",
                                    "date": "18/02/17",
                                    "amount": 2.88,
                                    "balanceAmount": 7789.41
                                },
                                {
                                    "particular": "NEFT CHGS INCL ST & CESS 200217",
                                    "date": "22/02/17",
                                    "amount": 2.88,
                                    "balanceAmount": 3505.78
                                },
                                {
                                    "particular": "NEFT CHGS INCL ST & CESS 210217",
                                    "date": "23/02/17",
                                    "amount": 2.88,
                                    "balanceAmount": 15002.9
                                }
                            ]
                        },
                        "17/06": {
                            "month": "17/06",
                            "amount": 14.399999999999999,
                            "count": 5,
                            "transactions": [
                                {
                                    "particular": "NEFT CHGS INCL ST & CESS 290517",
                                    "date": "01/06/17",
                                    "amount": 2.88,
                                    "balanceAmount": 3620.1
                                },
                                {
                                    "particular": "NEFT CHGS INCL ST & CESS 300517",
                                    "date": "01/06/17",
                                    "amount": 2.88,
                                    "balanceAmount": 3617.22
                                },
                                {
                                    "particular": "NEFT CHGS INCL ST & CESS 150617",
                                    "date": "21/06/17",
                                    "amount": 2.88,
                                    "balanceAmount": 3390.96
                                },
                                {
                                    "particular": "NEFT CHGS INCL ST & CESS 160617",
                                    "date": "22/06/17",
                                    "amount": 2.88,
                                    "balanceAmount": 3904.08
                                },
                                {
                                    "particular": "NEFT CHGS INCL ST & CESS 170617",
                                    "date": "23/06/17",
                                    "amount": 2.88,
                                    "balanceAmount": 14901.2
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "imps p2p 575 7",
                    "count": 6,
                    "amount": 34.5,
                    "monthlyTransactions": {
                        "17/02": {
                            "month": "17/02",
                            "amount": 17.25,
                            "count": 3,
                            "transactions": [
                                {
                                    "particular": "IMPS P2P 575 703211108906#01/02/ 040217",
                                    "date": "16/02/17",
                                    "amount": 5.75,
                                    "balanceAmount": 2049.04
                                },
                                {
                                    "particular": "IMPS P2P 575 703914329495#08/02/ 100217",
                                    "date": "17/02/17",
                                    "amount": 5.75,
                                    "balanceAmount": 5527.29
                                },
                                {
                                    "particular": "IMPS P2P 575 704612304375#15/02/ 160217",
                                    "date": "20/02/17",
                                    "amount": 5.75,
                                    "balanceAmount": 5135.16
                                }
                            ]
                        },
                        "17/03": {
                            "month": "17/03",
                            "amount": 5.75,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "IMPS P2P 575 7075111919#16/03/ 180317",
                                    "date": "22/03/17",
                                    "amount": 5.75,
                                    "balanceAmount": 9855.53
                                }
                            ]
                        },
                        "17/05": {
                            "month": "17/05",
                            "amount": 11.5,
                            "count": 2,
                            "transactions": [
                                {
                                    "particular": "IMPS P2P 575 712912173445#09/05/ 150517",
                                    "date": "23/05/17",
                                    "amount": 5.75,
                                    "balanceAmount": 15244.73
                                },
                                {
                                    "particular": "IMPS P2P 575 712916138399#09/05/ 150517",
                                    "date": "23/05/17",
                                    "amount": 5.75,
                                    "balanceAmount": 15238.98
                                }
                            ]
                        }
                    }
                }
            ],
            "highestAmount": 102000
        },
        "monthlyRecurringCredits": {
            "months": [
                "17/06",
                "17/05",
                "17/04",
                "17/03",
                "17/02",
                "17/01"
            ],
            "data": [
                {
                    "summary": "neft cr YESB00012307 DEMO technologies private limited ROHAN GANDHI",
                    "count": 115,
                    "amount": 208409,
                    "monthlyTransactions": {
                        "17/01": {
                            "month": "17/01",
                            "amount": 80396,
                            "count": 28,
                            "transactions": [
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17010247110093",
                                    "date": "02/01/17",
                                    "amount": 313,
                                    "balanceAmount": 8141.11
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17010348417669",
                                    "date": "03/01/17",
                                    "amount": 9280,
                                    "balanceAmount": 16911.11
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17010549892717",
                                    "date": "05/01/17",
                                    "amount": 4879,
                                    "balanceAmount": 11290.11
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17010550345082",
                                    "date": "05/01/17",
                                    "amount": 5183,
                                    "balanceAmount": 16473.11
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17010651453793",
                                    "date": "06/01/17",
                                    "amount": 679,
                                    "balanceAmount": 14512.11
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17010752406198",
                                    "date": "07/01/17",
                                    "amount": 4971,
                                    "balanceAmount": 14465.57
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17010953765743",
                                    "date": "09/01/17",
                                    "amount": 6082,
                                    "balanceAmount": 13292.19
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17011054754055",
                                    "date": "10/01/17",
                                    "amount": 5062,
                                    "balanceAmount": 13354.19
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17011155755279",
                                    "date": "11/01/17",
                                    "amount": 2860,
                                    "balanceAmount": 21214.19
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17011256672733",
                                    "date": "12/01/17",
                                    "amount": 1121,
                                    "balanceAmount": 17202.19
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17011357916127",
                                    "date": "13/01/17",
                                    "amount": 2710,
                                    "balanceAmount": 19906.44
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17011658971179",
                                    "date": "16/01/17",
                                    "amount": 1987,
                                    "balanceAmount": 15841.68
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17011659129732",
                                    "date": "16/01/17",
                                    "amount": 5324,
                                    "balanceAmount": 21165.68
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17011760024020",
                                    "date": "17/01/17",
                                    "amount": 3765,
                                    "balanceAmount": 12377.68
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17011962047989",
                                    "date": "19/01/17",
                                    "amount": 3782,
                                    "balanceAmount": 7994.68
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17012062777614",
                                    "date": "20/01/17",
                                    "amount": 1394,
                                    "balanceAmount": 9368.55
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17012163449269",
                                    "date": "21/01/17",
                                    "amount": 1410,
                                    "balanceAmount": 2708.05
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17012365118320",
                                    "date": "23/01/17",
                                    "amount": 3987,
                                    "balanceAmount": 4292.17
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17012467457083",
                                    "date": "24/01/17",
                                    "amount": 471,
                                    "balanceAmount": 4763.17
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17012568474845",
                                    "date": "25/01/17",
                                    "amount": 3171,
                                    "balanceAmount": 3584.17
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17012769758573",
                                    "date": "27/01/17",
                                    "amount": 306,
                                    "balanceAmount": 893.92
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17012769758565",
                                    "date": "27/01/17",
                                    "amount": 746,
                                    "balanceAmount": 1639.92
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17013071005087",
                                    "date": "30/01/17",
                                    "amount": 4422,
                                    "balanceAmount": 8456.16
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17013071005071",
                                    "date": "30/01/17",
                                    "amount": 274,
                                    "balanceAmount": 8730.16
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17013071179918",
                                    "date": "30/01/17",
                                    "amount": 591,
                                    "balanceAmount": 9321.16
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17013071179923",
                                    "date": "30/01/17",
                                    "amount": 627,
                                    "balanceAmount": 9948.16
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17013172396852",
                                    "date": "31/01/17",
                                    "amount": 3984,
                                    "balanceAmount": 13165.66
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17013172396856",
                                    "date": "31/01/17",
                                    "amount": 1015,
                                    "balanceAmount": 14180.66
                                }
                            ]
                        },
                        "17/02": {
                            "month": "17/02",
                            "amount": 38731,
                            "count": 26,
                            "transactions": [
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17020173659913",
                                    "date": "01/02/17",
                                    "amount": 2140,
                                    "balanceAmount": 8320.66
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17020173659920",
                                    "date": "01/02/17",
                                    "amount": 88,
                                    "balanceAmount": 8408.66
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17020274903533",
                                    "date": "02/02/17",
                                    "amount": 817,
                                    "balanceAmount": 6392.66
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17020274903537",
                                    "date": "02/02/17",
                                    "amount": 407,
                                    "balanceAmount": 6799.66
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17020376369318",
                                    "date": "03/02/17",
                                    "amount": 23,
                                    "balanceAmount": 6822.66
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17020376369315",
                                    "date": "03/02/17",
                                    "amount": 3607,
                                    "balanceAmount": 10429.66
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17020477394166",
                                    "date": "04/02/17",
                                    "amount": 3049,
                                    "balanceAmount": 13078.66
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17020477394168",
                                    "date": "04/02/17",
                                    "amount": 170,
                                    "balanceAmount": 13248.66
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17020678300541",
                                    "date": "06/02/17",
                                    "amount": 6209,
                                    "balanceAmount": 6957.66
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17020678300569",
                                    "date": "06/02/17",
                                    "amount": 127,
                                    "balanceAmount": 7084.66
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17020779415144",
                                    "date": "07/02/17",
                                    "amount": 32,
                                    "balanceAmount": 7116.66
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17020880671847",
                                    "date": "08/02/17",
                                    "amount": 1435,
                                    "balanceAmount": 36679.18
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17020981670464",
                                    "date": "09/02/17",
                                    "amount": 699,
                                    "balanceAmount": 28378.18
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-0P17021082649270",
                                    "date": "10/02/17",
                                    "amount": 578,
                                    "balanceAmount": 18956.18
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N044170000402513",
                                    "date": "14/02/17",
                                    "amount": 555,
                                    "balanceAmount": 14836.79
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N044170000446617",
                                    "date": "14/02/17",
                                    "amount": 2990,
                                    "balanceAmount": 17826.79
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N046170000935460",
                                    "date": "15/02/17",
                                    "amount": 876,
                                    "balanceAmount": 10202.79
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N047170001131925",
                                    "date": "16/02/17",
                                    "amount": 2484,
                                    "balanceAmount": 4533.04
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N048170001352611",
                                    "date": "17/02/17",
                                    "amount": 2265,
                                    "balanceAmount": 7792.29
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N049170001633323",
                                    "date": "18/02/17",
                                    "amount": 3088,
                                    "balanceAmount": 10877.41
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N051170001860911",
                                    "date": "20/02/17",
                                    "amount": 3608,
                                    "balanceAmount": 8743.16
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N052170002042538",
                                    "date": "21/02/17",
                                    "amount": 97,
                                    "balanceAmount": 2508.66
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N055170002725273",
                                    "date": "24/02/17",
                                    "amount": 1481,
                                    "balanceAmount": 2933.9
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N058170002987907",
                                    "date": "27/02/17",
                                    "amount": 1529,
                                    "balanceAmount": 1531.4
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N058170003031193",
                                    "date": "27/02/17",
                                    "amount": 120,
                                    "balanceAmount": 1651.4
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N059170003431347",
                                    "date": "28/02/17",
                                    "amount": 257,
                                    "balanceAmount": 308.4
                                }
                            ]
                        },
                        "17/03": {
                            "month": "17/03",
                            "amount": 2648,
                            "count": 3,
                            "transactions": [
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N060170003968976",
                                    "date": "01/03/17",
                                    "amount": 1025,
                                    "balanceAmount": 3167.4
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N061170004278791",
                                    "date": "02/03/17",
                                    "amount": 1185,
                                    "balanceAmount": 2078.4
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N090170010839288",
                                    "date": "31/03/17",
                                    "amount": 438,
                                    "balanceAmount": 4520.53
                                }
                            ]
                        },
                        "17/04": {
                            "month": "17/04",
                            "amount": 27776,
                            "count": 18,
                            "transactions": [
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N093170011561294",
                                    "date": "04/04/17",
                                    "amount": 1870,
                                    "balanceAmount": 7962.53
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N094170011763314",
                                    "date": "04/04/17",
                                    "amount": 1094,
                                    "balanceAmount": 14056.53
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N095170012088917",
                                    "date": "06/04/17",
                                    "amount": 670,
                                    "balanceAmount": 8868.8
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N097170012630056",
                                    "date": "07/04/17",
                                    "amount": 1236,
                                    "balanceAmount": 9904.8
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N100170013198880",
                                    "date": "11/04/17",
                                    "amount": 4298,
                                    "balanceAmount": 4616.97
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N101170013492727",
                                    "date": "12/04/17",
                                    "amount": 2881,
                                    "balanceAmount": 7497.97
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N102170013604373",
                                    "date": "12/04/17",
                                    "amount": 921,
                                    "balanceAmount": 10528.54
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N103170013889475",
                                    "date": "13/04/17",
                                    "amount": 4237,
                                    "balanceAmount": 14365.54
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N105170014237139",
                                    "date": "15/04/17",
                                    "amount": 2319,
                                    "balanceAmount": 16484.54
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N107170014489007",
                                    "date": "17/04/17",
                                    "amount": 200,
                                    "balanceAmount": 15134.04
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N109170014962855",
                                    "date": "19/04/17",
                                    "amount": 40,
                                    "balanceAmount": 12113.54
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N111170015372393",
                                    "date": "21/04/17",
                                    "amount": 1465,
                                    "balanceAmount": 14104.46
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N114170015728706",
                                    "date": "24/04/17",
                                    "amount": 2026,
                                    "balanceAmount": 17130.46
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N115170015929032",
                                    "date": "25/04/17",
                                    "amount": 1441,
                                    "balanceAmount": 4171.46
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N116170016143033",
                                    "date": "26/04/17",
                                    "amount": 212,
                                    "balanceAmount": 4383.46
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N117170016341484",
                                    "date": "27/04/17",
                                    "amount": 551,
                                    "balanceAmount": 2934.46
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N118170016541587",
                                    "date": "28/04/17",
                                    "amount": 1710,
                                    "balanceAmount": 4644.46
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N119170017004301",
                                    "date": "29/04/17",
                                    "amount": 605,
                                    "balanceAmount": 4394.96
                                }
                            ]
                        },
                        "17/05": {
                            "month": "17/05",
                            "amount": 33642,
                            "count": 22,
                            "transactions": [
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N122170017532001",
                                    "date": "02/05/17",
                                    "amount": 3346,
                                    "balanceAmount": 8106.96
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N123170017768306",
                                    "date": "03/05/17",
                                    "amount": 1742,
                                    "balanceAmount": 9676.46
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N124170018202778",
                                    "date": "04/05/17",
                                    "amount": 1797,
                                    "balanceAmount": 10473.46
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N125170018450032",
                                    "date": "05/05/17",
                                    "amount": 1255,
                                    "balanceAmount": 7228.46
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N126170018743743",
                                    "date": "06/05/17",
                                    "amount": 782,
                                    "balanceAmount": 7921.21
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N128170019015812",
                                    "date": "08/05/17",
                                    "amount": 3066,
                                    "balanceAmount": 8465.19
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N129170019319625",
                                    "date": "09/05/17",
                                    "amount": 1766,
                                    "balanceAmount": 2478.98
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N130170019515029",
                                    "date": "10/05/17",
                                    "amount": 1924,
                                    "balanceAmount": 3550.98
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N131170019670871",
                                    "date": "11/05/17",
                                    "amount": 1803,
                                    "balanceAmount": 4537.48
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N132170019927217",
                                    "date": "12/05/17",
                                    "amount": 1404,
                                    "balanceAmount": 5941.48
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N135170020354823",
                                    "date": "15/05/17",
                                    "amount": 1121,
                                    "balanceAmount": 7062.48
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N137170020771801",
                                    "date": "17/05/17",
                                    "amount": 2100,
                                    "balanceAmount": 6145.98
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N138170020989411",
                                    "date": "18/05/17",
                                    "amount": 598,
                                    "balanceAmount": 8143.98
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N139170021208598",
                                    "date": "19/05/17",
                                    "amount": 888,
                                    "balanceAmount": 3790.48
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N140170021426663",
                                    "date": "20/05/17",
                                    "amount": 1959,
                                    "balanceAmount": 5549.48
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N142170021578803",
                                    "date": "22/05/17",
                                    "amount": 94,
                                    "balanceAmount": 8051.98
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N143170021833935",
                                    "date": "23/05/17",
                                    "amount": 975,
                                    "balanceAmount": 16213.98
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N144170022153559",
                                    "date": "24/05/17",
                                    "amount": 827,
                                    "balanceAmount": 2640.98
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N145170022304061",
                                    "date": "25/05/17",
                                    "amount": 1837,
                                    "balanceAmount": 5067.98
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N146170022530805",
                                    "date": "26/05/17",
                                    "amount": 1702,
                                    "balanceAmount": 6769.98
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N149170022869237",
                                    "date": "29/05/17",
                                    "amount": 2539,
                                    "balanceAmount": 3038.98
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N151170023335468",
                                    "date": "31/05/17",
                                    "amount": 117,
                                    "balanceAmount": 4727.98
                                }
                            ]
                        },
                        "17/06": {
                            "month": "17/06",
                            "amount": 25216,
                            "count": 18,
                            "transactions": [
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N152170023871007",
                                    "date": "01/06/17",
                                    "amount": 195,
                                    "balanceAmount": 3622.98
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N153170024130727",
                                    "date": "02/06/17",
                                    "amount": 88,
                                    "balanceAmount": 1871.22
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N154170024388264",
                                    "date": "03/06/17",
                                    "amount": 1384,
                                    "balanceAmount": 3255.22
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N157170025107064",
                                    "date": "06/06/17",
                                    "amount": 1008,
                                    "balanceAmount": 1763.22
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N158170025429739",
                                    "date": "07/06/17",
                                    "amount": 667,
                                    "balanceAmount": 7430.22
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N159170025918718",
                                    "date": "08/06/17",
                                    "amount": 1508,
                                    "balanceAmount": 3327.18
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N163170026582541",
                                    "date": "12/06/17",
                                    "amount": 3883,
                                    "balanceAmount": 4623.23
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N164170026890830",
                                    "date": "13/06/17",
                                    "amount": 3014,
                                    "balanceAmount": 7437.23
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N165170027220545",
                                    "date": "14/06/17",
                                    "amount": 1234,
                                    "balanceAmount": 8071.23
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N166170027443753",
                                    "date": "15/06/17",
                                    "amount": 2183,
                                    "balanceAmount": 8254.23
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N167170027661493",
                                    "date": "16/06/17",
                                    "amount": 1923,
                                    "balanceAmount": 10177.23
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N168170027906691",
                                    "date": "17/06/17",
                                    "amount": 1609,
                                    "balanceAmount": 6786.23
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N170170028204596",
                                    "date": "19/06/17",
                                    "amount": 1446,
                                    "balanceAmount": 2646.23
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N171170028446509",
                                    "date": "20/06/17",
                                    "amount": 1255,
                                    "balanceAmount": 3301.23
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N173170028774012",
                                    "date": "22/06/17",
                                    "amount": 516,
                                    "balanceAmount": 3906.96
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N174170029139269",
                                    "date": "23/06/17",
                                    "amount": 579,
                                    "balanceAmount": 15480.2
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N178170029357228",
                                    "date": "27/06/17",
                                    "amount": 445,
                                    "balanceAmount": 3903.2
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES PRIVATE LIMITED-ROHAN GANDHI-N179170029675270",
                                    "date": "28/06/17",
                                    "amount": 2279,
                                    "balanceAmount": 6182.2
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "TELE communicatio hdfc",
                    "count": 8,
                    "amount": 72500,
                    "monthlyTransactions": {
                        "17/03": {
                            "month": "17/03",
                            "amount": 61500,
                            "count": 6,
                            "transactions": [
                                {
                                    "particular": "IMPS-706618944660-TELE COMMUNICATIO-HDFC--PERSONAL",
                                    "date": "07/03/17",
                                    "amount": 2000,
                                    "balanceAmount": 3784.9
                                },
                                {
                                    "particular": "IMPS-82777281924-TELE COMMUNICATIO-HDFC--PERSONAL",
                                    "date": "08/03/17",
                                    "amount": 50000,
                                    "balanceAmount": 53784.9
                                },
                                {
                                    "particular": "IMPS-708118187617-TELE COMMUNICATIO-HDFC--PERSONAL",
                                    "date": "22/03/17",
                                    "amount": 3000,
                                    "balanceAmount": 14967.53
                                },
                                {
                                    "particular": "IMPS-708121236527-TELE COMMUNICATIO-HDFC--PERSONAL",
                                    "date": "22/03/17",
                                    "amount": 500,
                                    "balanceAmount": 14868.53
                                },
                                {
                                    "particular": "IMPS-708216437458-TELE COMMUNICATIO-HDFC--PERONAL",
                                    "date": "23/03/17",
                                    "amount": 1000,
                                    "balanceAmount": 15006.03
                                },
                                {
                                    "particular": "IMPS-708411917680-TELE COMMUNICATIO-HDFC--",
                                    "date": "25/03/17",
                                    "amount": 5000,
                                    "balanceAmount": 21847.03
                                }
                            ]
                        },
                        "17/04": {
                            "month": "17/04",
                            "amount": 11000,
                            "count": 2,
                            "transactions": [
                                {
                                    "particular": "IMPS-711016847331-TELE COMMUNICATIO-HDFC--EMI",
                                    "date": "20/04/17",
                                    "amount": 10000,
                                    "balanceAmount": 22113.54
                                },
                                {
                                    "particular": "IMPS-711220586245-TELE COMMUNICATIO-HDFC--EMI",
                                    "date": "22/04/17",
                                    "amount": 1000,
                                    "balanceAmount": 15104.46
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "hdfc xxxxxxxx",
                    "count": 19,
                    "amount": 53364,
                    "monthlyTransactions": {
                        "17/01": {
                            "month": "17/01",
                            "amount": 12000,
                            "count": 3,
                            "transactions": [
                                {
                                    "particular": "IMPS-702215406549-ROHAN-HDFC-XXXXXXXX9798-177233421",
                                    "date": "22/01/17",
                                    "amount": 5000,
                                    "balanceAmount": 7708.05
                                },
                                {
                                    "particular": "IMPS-702217552343-ROHAN-HDFC-XXXXXXXX9798-177258964",
                                    "date": "22/01/17",
                                    "amount": 5000,
                                    "balanceAmount": 12708.05
                                },
                                {
                                    "particular": "IMPS-702218626937-ROHAN-HDFC-XXXXXXXX9798-177276456",
                                    "date": "22/01/17",
                                    "amount": 2000,
                                    "balanceAmount": 14708.05
                                }
                            ]
                        },
                        "17/02": {
                            "month": "17/02",
                            "amount": 11500,
                            "count": 3,
                            "transactions": [
                                {
                                    "particular": "IMPS-705319767305-ROHAN-HDFC-XXXXXXXX9798-194745835",
                                    "date": "22/02/17",
                                    "amount": 5000,
                                    "balanceAmount": 8505.78
                                },
                                {
                                    "particular": "IMPS-705319792110-ROHAN-HDFC-XXXXXXXX9798-194755705",
                                    "date": "22/02/17",
                                    "amount": 5000,
                                    "balanceAmount": 13505.78
                                },
                                {
                                    "particular": "IMPS-705319796972-ROHAN-HDFC-XXXXXXXX9798-194757501",
                                    "date": "22/02/17",
                                    "amount": 1500,
                                    "balanceAmount": 15005.78
                                }
                            ]
                        },
                        "17/04": {
                            "month": "17/04",
                            "amount": 2614,
                            "count": 4,
                            "transactions": [
                                {
                                    "particular": "IMPS-709315771723-ROHAN-HDFC-XXXXXXXX3511-G",
                                    "date": "03/04/17",
                                    "amount": 1,
                                    "balanceAmount": 4092.53
                                },
                                {
                                    "particular": "IMPS-710516051132-ROHAN GANDHI-HDFC-XXXXXXXX0602-FT170415161034251315",
                                    "date": "15/04/17",
                                    "amount": 719,
                                    "balanceAmount": 17203.54
                                },
                                {
                                    "particular": "IMPS-710516050756-ROHAN GANDHI-HDFC-XXXXXXXX0602-FT170415161034219799",
                                    "date": "15/04/17",
                                    "amount": 599,
                                    "balanceAmount": 17802.54
                                },
                                {
                                    "particular": "IMPS-710718442061-ROHAN GANDHI-HDFC-XXXXXXXX0602-FT170417185409831875",
                                    "date": "17/04/17",
                                    "amount": 1295,
                                    "balanceAmount": 16429.04
                                }
                            ]
                        },
                        "17/05": {
                            "month": "17/05",
                            "amount": 14250,
                            "count": 5,
                            "transactions": [
                                {
                                    "particular": "IMPS-714214815889-ROHAN-HDFC-XXXXXXXX9798-254105286",
                                    "date": "22/05/17",
                                    "amount": 5000,
                                    "balanceAmount": 7707.98
                                },
                                {
                                    "particular": "IMPS-714214819619-ROHAN-HDFC-XXXXXXXX9798-254106800",
                                    "date": "22/05/17",
                                    "amount": 250,
                                    "balanceAmount": 7957.98
                                },
                                {
                                    "particular": "IMPS-714309052193-ROHAN-HDFC-XXXXXXXX9798-254636381",
                                    "date": "23/05/17",
                                    "amount": 5000,
                                    "balanceAmount": 12051.98
                                },
                                {
                                    "particular": "IMPS-714309053205-ROHAN-HDFC-XXXXXXXX9798-254636886",
                                    "date": "23/05/17",
                                    "amount": 3000,
                                    "balanceAmount": 15051.98
                                },
                                {
                                    "particular": "IMPS-714309105747-ROHAN-HDFC-XXXXXXXX9798-254665502",
                                    "date": "23/05/17",
                                    "amount": 1000,
                                    "balanceAmount": 16051.98
                                }
                            ]
                        },
                        "17/06": {
                            "month": "17/06",
                            "amount": 13000,
                            "count": 4,
                            "transactions": [
                                {
                                    "particular": "IMPS-716819288520-ROHAN-HDFC-XXXXXXXX9798-274769970",
                                    "date": "17/06/17",
                                    "amount": 2000,
                                    "balanceAmount": 2674.73
                                },
                                {
                                    "particular": "IMPS-717320066251-ROHAN-HDFC-XXXXXXXX9798-278944222",
                                    "date": "22/06/17",
                                    "amount": 5000,
                                    "balanceAmount": 8904.08
                                },
                                {
                                    "particular": "IMPS-717321073527-ROHAN-HDFC-XXXXXXXX9798-278948544",
                                    "date": "22/06/17",
                                    "amount": 5000,
                                    "balanceAmount": 13904.08
                                },
                                {
                                    "particular": "IMPS-717321074412-ROHAN-HDFC-XXXXXXXX9798-278948945",
                                    "date": "22/06/17",
                                    "amount": 1000,
                                    "balanceAmount": 14904.08
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "ROHAN GANDHI hdfc xxxxxxxxsdrr p2botp_",
                    "count": 22,
                    "amount": 49754,
                    "monthlyTransactions": {
                        "17/01": {
                            "month": "17/01",
                            "amount": 3550,
                            "count": 2,
                            "transactions": [
                                {
                                    "particular": "IMPS-702512381887-ROHAN GANDHI-HDFC-XXXXXXXXSDRR-P2BOTP_43BB489633E49D0E",
                                    "date": "25/01/17",
                                    "amount": 1150,
                                    "balanceAmount": 3413.17
                                },
                                {
                                    "particular": "IMPS-702813953625-ROHAN GANDHI-HDFC-XXXXXXXXSDRR-P2BOTP_F9F64FDC23B62AD5",
                                    "date": "28/01/17",
                                    "amount": 2400,
                                    "balanceAmount": 4039.92
                                }
                            ]
                        },
                        "17/02": {
                            "month": "17/02",
                            "amount": 13950,
                            "count": 8,
                            "transactions": [
                                {
                                    "particular": "IMPS-703210347342-ROHAN GANDHI-HDFC-XXXXXXXXSDRR-P2BOTP_11FE4082C2B201EE",
                                    "date": "01/02/17",
                                    "amount": 2000,
                                    "balanceAmount": 16180.66
                                },
                                {
                                    "particular": "IMPS-703513939703-ROHAN GANDHI-HDFC-XXXXXXXXSDRR-P2BOTP_202838D0E3A54F9A",
                                    "date": "04/02/17",
                                    "amount": 600,
                                    "balanceAmount": 10029.66
                                },
                                {
                                    "particular": "IMPS-704516103892-ROHAN GANDHI-HDFC-XXXXXXXXSDRR-P2BOTP_1EEC6DE4EA94A580",
                                    "date": "14/02/17",
                                    "amount": 1500,
                                    "balanceAmount": 19326.79
                                },
                                {
                                    "particular": "IMPS-704917253763-ROHAN GANDHI-HDFC-XXXXXXXXSDRR-P2BOTP_092071DFDAB1898A",
                                    "date": "18/02/17",
                                    "amount": 5000,
                                    "balanceAmount": 15877.41
                                },
                                {
                                    "particular": "IMPS-705018591043-ROHAN GANDHI-HDFC-XXXXXXXXSDRR-P2BOTP_BD7686E308B2E0C0",
                                    "date": "19/02/17",
                                    "amount": 2000,
                                    "balanceAmount": 15140.91
                                },
                                {
                                    "particular": "IMPS-705212990528-ROHAN GANDHI-HDFC-XXXXXXXXSDRR-P2BOTP_0A6BEE7A46343725",
                                    "date": "21/02/17",
                                    "amount": 1100,
                                    "balanceAmount": 10508.16
                                },
                                {
                                    "particular": "IMPS-705310622105-ROHAN GANDHI-HDFC-XXXXXXXXSDRR-P2BOTP_E224D0841D3D6458",
                                    "date": "22/02/17",
                                    "amount": 1000,
                                    "balanceAmount": 3508.66
                                },
                                {
                                    "particular": "IMPS-705612457299-ROHAN GANDHI-HDFC-XXXXXXXXSDRR-P2BOTP_9F674950862E3DF8",
                                    "date": "25/02/17",
                                    "amount": 750,
                                    "balanceAmount": 2422.4
                                }
                            ]
                        },
                        "17/03": {
                            "month": "17/03",
                            "amount": 1834,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "IMPS-706016466199-ROHAN GANDHI-HDFC-XXXXXXXXSDRR-P2BOTP_342D080799EC6DBE",
                                    "date": "01/03/17",
                                    "amount": 1834,
                                    "balanceAmount": 2142.4
                                }
                            ]
                        },
                        "17/04": {
                            "month": "17/04",
                            "amount": 9500,
                            "count": 2,
                            "transactions": [
                                {
                                    "particular": "IMPS-709412070538-ROHAN GANDHI-HDFC-XXXXXXXXSDRR-P2BOTP_78FBF92351D1395C",
                                    "date": "04/04/17",
                                    "amount": 5000,
                                    "balanceAmount": 12962.53
                                },
                                {
                                    "particular": "IMPS-710912309393-ROHAN GANDHI-HDFC-XXXXXXXXSDRR-P2BOTP_71133AC497365F33",
                                    "date": "19/04/17",
                                    "amount": 4500,
                                    "balanceAmount": 12073.54
                                }
                            ]
                        },
                        "17/05": {
                            "month": "17/05",
                            "amount": 13920,
                            "count": 7,
                            "transactions": [
                                {
                                    "particular": "IMPS-712118580993-ROHAN GANDHI-HDFC-XXXXXXXXSDRR-P2BOTP_A04B319DD1D5F971",
                                    "date": "01/05/17",
                                    "amount": 2500,
                                    "balanceAmount": 6594.96
                                },
                                {
                                    "particular": "IMPS-712621949007-ROHAN GANDHI-HDFC-XXXXXXXXSDRR-P2BOTP_E489EB9E69EE6BD0",
                                    "date": "06/05/17",
                                    "amount": 3000,
                                    "balanceAmount": 6815.21
                                },
                                {
                                    "particular": "IMPS-712916466815-ROHAN GANDHI-HDFC-XXXXXXXXSDRR-P2BOTP_C03DF926607D3A44",
                                    "date": "09/05/17",
                                    "amount": 1300,
                                    "balanceAmount": 4926.98
                                },
                                {
                                    "particular": "IMPS-713717039402-ROHAN GANDHI-HDFC-XXXXXXXXSDRR-P2BOTP_6A2BA42B5D1A6DB1",
                                    "date": "17/05/17",
                                    "amount": 1400,
                                    "balanceAmount": 7545.98
                                },
                                {
                                    "particular": "IMPS-714914233305-ROHAN GANDHI-HDFC-XXXXXXXXSDRR-P2BOTP_B06C7F9EE0CC9F0A",
                                    "date": "29/05/17",
                                    "amount": 5000,
                                    "balanceAmount": 8038.98
                                },
                                {
                                    "particular": "IMPS-715113846314-ROHAN GANDHI-HDFC-XXXXXXXXSDRR-P2BOTP_855ABAA195C84CEA",
                                    "date": "31/05/17",
                                    "amount": 150,
                                    "balanceAmount": 4040.98
                                },
                                {
                                    "particular": "IMPS-715113853929-ROHAN GANDHI-HDFC-XXXXXXXXSDRR-P2BOTP_20E4CABC2E2E4A93",
                                    "date": "31/05/17",
                                    "amount": 570,
                                    "balanceAmount": 4610.98
                                }
                            ]
                        },
                        "17/06": {
                            "month": "17/06",
                            "amount": 7000,
                            "count": 2,
                            "transactions": [
                                {
                                    "particular": "IMPS-715609959811-ROHAN GANDHI-HDFC-XXXXXXXXSDRR-P2BOTP_C3140B82EFA55F16",
                                    "date": "05/06/17",
                                    "amount": 2000,
                                    "balanceAmount": 5255.22
                                },
                                {
                                    "particular": "IMPS-715719065544-ROHAN GANDHI-HDFC-XXXXXXXXSDRR-P2BOTP_DCFF26126D09C545",
                                    "date": "06/06/17",
                                    "amount": 5000,
                                    "balanceAmount": 6763.22
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "neft cr YESB00012307 DEMO technologies ROHAN GANDHI n0",
                    "count": 21,
                    "amount": 28504,
                    "monthlyTransactions": {
                        "17/03": {
                            "month": "17/03",
                            "amount": 28504,
                            "count": 21,
                            "transactions": [
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES-ROHAN GANDHI-N062170004643473",
                                    "date": "03/03/17",
                                    "amount": 477,
                                    "balanceAmount": 2555.4
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES-ROHAN GANDHI-N063170004911967",
                                    "date": "04/03/17",
                                    "amount": 2036,
                                    "balanceAmount": 4591.4
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES-ROHAN GANDHI-N065170005187593",
                                    "date": "06/03/17",
                                    "amount": 1095,
                                    "balanceAmount": 4984.9
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES-ROHAN GANDHI-N066170005496230",
                                    "date": "07/03/17",
                                    "amount": 1300,
                                    "balanceAmount": 6284.9
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES-ROHAN GANDHI-N067170005930884",
                                    "date": "08/03/17",
                                    "amount": 114,
                                    "balanceAmount": 28325.09
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES-ROHAN GANDHI-N068170006204725",
                                    "date": "09/03/17",
                                    "amount": 1583,
                                    "balanceAmount": 29212.59
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES-ROHAN GANDHI-N069170006480256",
                                    "date": "10/03/17",
                                    "amount": 309,
                                    "balanceAmount": 9521.59
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES-ROHAN GANDHI-N072170006758240",
                                    "date": "13/03/17",
                                    "amount": 940,
                                    "balanceAmount": 10461.59
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES-ROHAN GANDHI-N074170007277910",
                                    "date": "15/03/17",
                                    "amount": 455,
                                    "balanceAmount": 10116.28
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES-ROHAN GANDHI-N075170007518924",
                                    "date": "16/03/17",
                                    "amount": 1147,
                                    "balanceAmount": 7263.28
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES-ROHAN GANDHI-N076170007711587",
                                    "date": "17/03/17",
                                    "amount": 1661,
                                    "balanceAmount": 8924.28
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES-ROHAN GANDHI-N077170008066325",
                                    "date": "18/03/17",
                                    "amount": 464,
                                    "balanceAmount": 8789.28
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES-ROHAN GANDHI-N079170008299710",
                                    "date": "20/03/17",
                                    "amount": 1674,
                                    "balanceAmount": 10463.28
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES-ROHAN GANDHI-N080170008529414",
                                    "date": "21/03/17",
                                    "amount": 397,
                                    "balanceAmount": 10860.28
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES-ROHAN GANDHI-N081170008741519",
                                    "date": "22/03/17",
                                    "amount": 2112,
                                    "balanceAmount": 11967.53
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES-ROHAN GANDHI-N082170009030583",
                                    "date": "23/03/17",
                                    "amount": 1122,
                                    "balanceAmount": 16128.03
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES-ROHAN GANDHI-N083170009304348",
                                    "date": "24/03/17",
                                    "amount": 719,
                                    "balanceAmount": 16847.03
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES-ROHAN GANDHI-N086170009666108",
                                    "date": "27/03/17",
                                    "amount": 3327,
                                    "balanceAmount": 7512.03
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES-ROHAN GANDHI-N087170010038439",
                                    "date": "28/03/17",
                                    "amount": 5009,
                                    "balanceAmount": 12521.03
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES-ROHAN GANDHI-N088170010250782",
                                    "date": "29/03/17",
                                    "amount": 962,
                                    "balanceAmount": 13483.03
                                },
                                {
                                    "particular": "NEFT CR-YESB00012307-DEMO TECHNOLOGIES-ROHAN GANDHI-N089170010476856",
                                    "date": "30/03/17",
                                    "amount": 1601,
                                    "balanceAmount": 14082.53
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "imps p2a 70",
                    "count": 5,
                    "amount": 23000,
                    "monthlyTransactions": {
                        "17/01": {
                            "month": "17/01",
                            "amount": 23000,
                            "count": 5,
                            "transactions": [
                                {
                                    "particular": "IMPS-P2A-700916126141-919818921636-170610419",
                                    "date": "09/01/17",
                                    "amount": 5000,
                                    "balanceAmount": 8213.07
                                },
                                {
                                    "particular": "IMPS-P2A-700916127733-919818921636-170611002",
                                    "date": "09/01/17",
                                    "amount": 5000,
                                    "balanceAmount": 13213.07
                                },
                                {
                                    "particular": "IMPS-P2A-700916127801-919818921636-170611051",
                                    "date": "09/01/17",
                                    "amount": 5000,
                                    "balanceAmount": 18213.07
                                },
                                {
                                    "particular": "IMPS-P2A-700916127867-919818921636-170611054",
                                    "date": "09/01/17",
                                    "amount": 5000,
                                    "balanceAmount": 23213.07
                                },
                                {
                                    "particular": "IMPS-P2A-701617915637-918901059606-174295482",
                                    "date": "16/01/17",
                                    "amount": 3000,
                                    "balanceAmount": 13854.68
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "SURYA rathi idib xxxxxx2713 load",
                    "count": 1,
                    "amount": 5000,
                    "monthlyTransactions": {
                        "17/02": {
                            "month": "17/02",
                            "amount": 5000,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "REV--IMPS-703312102642-SURYA RATHI-IDIB-XXXXXX2713-LOAD",
                                    "date": "02/02/17",
                                    "amount": 5000,
                                    "balanceAmount": 7575.66
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "irctc_cris ref",
                    "count": 7,
                    "amount": 4351.5,
                    "monthlyTransactions": {
                        "17/02": {
                            "month": "17/02",
                            "amount": 665,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "IRCTC_CRIS REF-19/02/17-100000749518828",
                                    "date": "20/02/17",
                                    "amount": 665,
                                    "balanceAmount": 9408.16
                                }
                            ]
                        },
                        "17/03": {
                            "month": "17/03",
                            "amount": 530,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "IRCTC_CRIS REF-05/03/17-100000764874585",
                                    "date": "08/03/17",
                                    "amount": 530,
                                    "balanceAmount": 28211.09
                                }
                            ]
                        },
                        "17/04": {
                            "month": "17/04",
                            "amount": 1091.5,
                            "count": 2,
                            "transactions": [
                                {
                                    "particular": "IRCTC_CRIS REF-17/04/17-100000809967866",
                                    "date": "18/04/17",
                                    "amount": 11.5,
                                    "balanceAmount": 6493.54
                                },
                                {
                                    "particular": "IRCTC_CRIS REF-17/04/17-100000809967866",
                                    "date": "18/04/17",
                                    "amount": 1080,
                                    "balanceAmount": 7573.54
                                }
                            ]
                        },
                        "17/05": {
                            "month": "17/05",
                            "amount": 2065,
                            "count": 3,
                            "transactions": [
                                {
                                    "particular": "IRCTC_CRIS REF-17/05/17-100000843023118",
                                    "date": "18/05/17",
                                    "amount": 745,
                                    "balanceAmount": 8888.98
                                },
                                {
                                    "particular": "IRCTC_CRIS REF-22/05/17-100000848921380",
                                    "date": "24/05/17",
                                    "amount": 590,
                                    "balanceAmount": 3230.98
                                },
                                {
                                    "particular": "IRCTC_CRIS REF-23/05/17-100000849785885",
                                    "date": "26/05/17",
                                    "amount": 730,
                                    "balanceAmount": 7499.98
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "neft cr deut0784bby uber india systems pltd ROHAN GANDHI 170",
                    "count": 3,
                    "amount": 2844.4500000000003,
                    "monthlyTransactions": {
                        "17/04": {
                            "month": "17/04",
                            "amount": 2751.84,
                            "count": 2,
                            "transactions": [
                                {
                                    "particular": "NEFT CR-DEUT0784BBY-UBER INDIA SYSTEMS PLTD-ROHAN GANDHI-170405047GN02782",
                                    "date": "05/04/17",
                                    "amount": 642.27,
                                    "balanceAmount": 12698.8
                                },
                                {
                                    "particular": "NEFT CR-DEUT0784BBY-UBER INDIA SYSTEMS PLTD-ROHAN GANDHI-170412051GN07679",
                                    "date": "12/04/17",
                                    "amount": 2109.57,
                                    "balanceAmount": 9607.54
                                }
                            ]
                        },
                        "17/06": {
                            "month": "17/06",
                            "amount": 92.61,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "NEFT CR-DEUT0784BBY-UBER INDIA SYSTEMS PLTD-ROHAN GANDHI-170621041GN01848",
                                    "date": "21/06/17",
                                    "amount": 92.61,
                                    "balanceAmount": 3393.84
                                }
                            ]
                        }
                    }
                },
                {
                    "summary": "manoj hdfc xxxxxxxx9798",
                    "count": 2,
                    "amount": 2201,
                    "monthlyTransactions": {
                        "17/02": {
                            "month": "17/02",
                            "amount": 1001,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "IMPS-703310984800-MANOJ-HDFC-XXXXXXXX9798-182861739",
                                    "date": "02/02/17",
                                    "amount": 1001,
                                    "balanceAmount": 9409.66
                                }
                            ]
                        },
                        "17/04": {
                            "month": "17/04",
                            "amount": 1200,
                            "count": 1,
                            "transactions": [
                                {
                                    "particular": "IMPS-709910104818-MANOJ-HDFC-XXXXXXXX9798-222416045",
                                    "date": "09/04/17",
                                    "amount": 1200,
                                    "balanceAmount": 2466.19
                                }
                            ]
                        }
                    }
                }
            ],
            "highestAmount": 208409
        },
        "autoDebits": {
            "autoDebitsByName": [
                {
                    "name": "CC XXXXXX AUTOPAY SI TAD",
                    "numberOfSuccessfulPayments": 0,
                    "totalAmountPaid": 0,
                    "numberOfDefaults": 1,
                    "value": 14587.14,
                    "color": "rgba(21,94,190,1)"
                },
                {
                    "name": "ACH D  AUFINANCIERSINDIALTD LVPTU ",
                    "numberOfSuccessfulPayments": 5,
                    "totalAmountPaid": 72000,
                    "numberOfDefaults": 1,
                    "value": 14400,
                    "color": "rgba(21,94,190,0.75)"
                },
                {
                    "name": "CC XXXXXX AUTOPAY SI TAD",
                    "numberOfSuccessfulPayments": 0,
                    "totalAmountPaid": 0,
                    "numberOfDefaults": 1,
                    "value": 8557.14,
                    "color": "rgba(21,94,190,0.67)"
                },
                {
                    "name": "BAJAJFINEMI BF  ",
                    "numberOfSuccessfulPayments": 4,
                    "totalAmountPaid": 18000,
                    "numberOfDefaults": 1,
                    "value": 4500,
                    "color": "rgba(21,94,190,0.59)"
                },
                {
                    "name": "BAJAJ FINEMI BF  ",
                    "numberOfSuccessfulPayments": 3,
                    "totalAmountPaid": 5502,
                    "numberOfDefaults": 0,
                    "value": 1834,
                    "color": "rgba(21,94,190,0.51)"
                }
            ],
            "autoDebitsByMonth": [
                {
                    "14400": 14400,
                    "month": "17/01"
                },
                {
                    "14400": 14400,
                    "14587.14": 14587.14,
                    "8557.14": 8557.14,
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
                },
                {
                    "1834": 1834,
                    "4500": 4500,
                    "14400": 14400,
                    "month": "17/05"
                },
                {
                    "1834": 1834,
                    "4500": 4500,
                    "14400": 14400,
                    "month": "17/06"
                }
            ],
            "allTransactions": [
                {
                    "date": "23/01/17",
                    "autoDebitAmount": 14400,
                    "balanceAmount": 305.17,
                    "particular": "ACH D- AUFINANCIERSINDIALTD-LVPTU04016-1",
                    "type": "DEBIT",
                    "category": [
                        "Payment",
                        "Loan"
                    ]
                },
                {
                    "date": "08/02/17",
                    "autoDebitAmount": 14587.14,
                    "balanceAmount": -7455.82,
                    "particular": "CC 0004112442XXXXXX8872 AUTOPAY SI-TAD",
                    "type": "DEFAULT",
                    "category": [
                        "Payment",
                        "Credit Card"
                    ]
                },
                {
                    "date": "08/02/17",
                    "autoDebitAmount": 8557.14,
                    "balanceAmount": -3425.82,
                    "particular": "CC 0004112442XXXXXX8872 AUTOPAY SI-TAD",
                    "type": "DEFAULT",
                    "category": [
                        "Payment",
                        "Credit Card"
                    ]
                },
                {
                    "date": "23/02/17",
                    "autoDebitAmount": 14400,
                    "balanceAmount": 602.9,
                    "particular": "ACH D- AUFINANCIERSINDIALTD-LVPTU04016-1",
                    "type": "DEBIT",
                    "category": [
                        "Payment",
                        "Loan"
                    ]
                },
                {
                    "date": "06/03/17",
                    "autoDebitAmount": 4500,
                    "balanceAmount": -610.1,
                    "particular": "BAJAJFINEMI-BF-1189499-55990",
                    "type": "DEFAULT",
                    "category": [
                        "Payment",
                        "Loan"
                    ]
                },
                {
                    "date": "07/03/17",
                    "autoDebitAmount": 4500,
                    "balanceAmount": 1784.9,
                    "particular": "BAJAJFINEMI-BF-1189499-7230",
                    "type": "DEBIT",
                    "category": [
                        "Payment",
                        "Loan"
                    ]
                },
                {
                    "date": "23/03/17",
                    "autoDebitAmount": 14400,
                    "balanceAmount": -393.97,
                    "particular": "ACH D- AUFINANCIERSINDIALTD-LVPTU04016-1",
                    "type": "DEFAULT",
                    "category": [
                        "Payment",
                        "Loan"
                    ]
                },
                {
                    "date": "03/04/17",
                    "autoDebitAmount": 1834,
                    "balanceAmount": 4091.53,
                    "particular": "BAJAJ FINEMI-BF-1189499-51163",
                    "type": "DEBIT",
                    "category": [
                        "Payment",
                        "Loan"
                    ]
                },
                {
                    "date": "05/04/17",
                    "autoDebitAmount": 4500,
                    "balanceAmount": 8198.8,
                    "particular": "BAJAJ FINEMI-BF-1189499-43484",
                    "type": "DEBIT",
                    "category": [
                        "Payment",
                        "Loan"
                    ]
                },
                {
                    "date": "24/04/17",
                    "autoDebitAmount": 14400,
                    "balanceAmount": 2730.46,
                    "particular": "ACH D- AUFINANCIERSINDIALTD-LVPTU04016-1",
                    "type": "DEBIT",
                    "category": [
                        "Payment",
                        "Loan"
                    ]
                },
                {
                    "date": "02/05/17",
                    "autoDebitAmount": 1834,
                    "balanceAmount": 4760.96,
                    "particular": "BAJAJ FINEMI-BF-1189499-49939",
                    "type": "DEBIT",
                    "category": [
                        "Payment",
                        "Loan"
                    ]
                },
                {
                    "date": "05/05/17",
                    "autoDebitAmount": 4500,
                    "balanceAmount": 5973.46,
                    "particular": "BAJAJ FINEMI-BF-1189499-35828",
                    "type": "DEBIT",
                    "category": [
                        "Payment",
                        "Loan"
                    ]
                },
                {
                    "date": "23/05/17",
                    "autoDebitAmount": 14400,
                    "balanceAmount": 1813.98,
                    "particular": "ACH D- AUFINANCIERS-LVPTU04016-170458917",
                    "type": "DEBIT",
                    "category": [
                        "Payment",
                        "Loan"
                    ]
                },
                {
                    "date": "02/06/17",
                    "autoDebitAmount": 1834,
                    "balanceAmount": 1783.22,
                    "particular": "BAJAJ FINEMI-BF-1189499-216580",
                    "type": "DEBIT",
                    "category": [
                        "Payment",
                        "Loan"
                    ]
                },
                {
                    "date": "05/06/17",
                    "autoDebitAmount": 4500,
                    "balanceAmount": 755.22,
                    "particular": "BAJAJ FINEMI-BF-1189499-80864",
                    "type": "DEBIT",
                    "category": [
                        "Payment",
                        "Loan"
                    ]
                },
                {
                    "date": "23/06/17",
                    "autoDebitAmount": 14400,
                    "balanceAmount": 1080.2,
                    "particular": "ACH D- AUFINANCIERS-9001020101524623",
                    "type": "DEBIT",
                    "category": [
                        "Payment",
                        "Loan"
                    ]
                }
            ]
        },
        "defaults": {
            "summary": {
                "amount": 42044.28,
                "count": 4
            },
            "allDefaults": [
                {
                    "balanceAmount": 7131.32,
                    "date": "08/02/17",
                    "defaultAmount": 14587.14,
                    "particular": "CC 0004112442XXXXXX8872 AUTOPAY SI-TAD",
                    "category": [
                        "Payment",
                        "Credit Card"
                    ]
                },
                {
                    "balanceAmount": 5131.32,
                    "date": "08/02/17",
                    "defaultAmount": 8557.14,
                    "particular": "CC 0004112442XXXXXX8872 AUTOPAY SI-TAD",
                    "category": [
                        "Payment",
                        "Credit Card"
                    ]
                },
                {
                    "balanceAmount": 3889.9,
                    "date": "06/03/17",
                    "defaultAmount": 4500,
                    "particular": "BAJAJFINEMI-BF-1189499-55990",
                    "category": [
                        "Payment",
                        "Loan"
                    ]
                },
                {
                    "balanceAmount": 14006.03,
                    "date": "23/03/17",
                    "defaultAmount": 14400,
                    "particular": "ACH D- AUFINANCIERSINDIALTD-LVPTU04016-1",
                    "category": [
                        "Payment",
                        "Loan"
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
            },
            {
                "average": 9793,
                "change": {
                    "amount": -670,
                    "percent": "-6.40"
                },
                "endDate": 31,
                "monthKey": "17/03",
                "startDate": 1
            },
            {
                "average": 8341,
                "change": {
                    "amount": -1452,
                    "percent": "-14.83"
                },
                "endDate": 30,
                "monthKey": "17/04",
                "startDate": 1
            },
            {
                "average": 5709,
                "change": {
                    "amount": -2632,
                    "percent": "-31.55"
                },
                "endDate": 31,
                "monthKey": "17/05",
                "startDate": 1
            },
            {
                "average": 3994,
                "change": {
                    "amount": -1715,
                    "percent": "-30.04"
                },
                "endDate": 29,
                "monthKey": "17/06",
                "startDate": 1
            }
        ],
        "monthlyGrossIncome": [
            {
                "month": "17/01",
                "credit": 125455,
                "debit": 124102,
                "autoDebit": 14400
            },
            {
                "month": "17/02",
                "credit": 155856,
                "debit": 169728,
                "autoDebit": 37544
            },
            {
                "month": "17/03",
                "credit": 115065,
                "debit": 110853,
                "autoDebit": 23400
            },
            {
                "month": "17/04",
                "credit": 82869,
                "debit": 83295,
                "autoDebit": 20734
            },
            {
                "month": "17/05",
                "credit": 65025,
                "debit": 65692,
                "autoDebit": 20734
            },
            {
                "month": "17/06",
                "credit": 48852,
                "debit": 44932,
                "autoDebit": 20734
            }
        ],
        "checkingSummary": {
            "beginningBalance": 12828.11,
            "depositsAndAdditions": {
                "instances": 221,
                "amount": 551077.37
            },
            "checksPaid": {
                "instances": 3,
                "amount": 17130
            },
            "atmWithdrawals": {
                "instances": 14,
                "amount": 68000
            },
            "bankFees": {
                "instances": 26,
                "amount": 1391.6
            },
            "electronicWithdrawals": {
                "instances": 154,
                "amount": 455072.68
            },
            "otherWithdrawals": {
                "instances": 6,
                "amount": 14964
            },
            "endingBalance": {
                "instances": 424,
                "amount": 7347.2
            }
        },
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
access-id | your_access_id
access-key | your_access_key



### Body
Parameter | Required | Description
--------- | ------- | -----------
bank | true | bank code obtained from supported banks api above
statement | true | bank statement file to be analysed
borrowerId | true | id of the borrower created earlier
pdfPassword | false | password of the pdf

## Reanalyse bank statement
`POST https://beta.inkredo.in/api/v0/parser/reanalyse/`

### Body
`{"borrowerId":"5bb20ba98b583b0b9cf1e13b"}`

### Headers
Name | Value
---|---
Content-Type | application/json
access-id | your_access_id
access-key | your_access_key

### Response
same as the parser api


## Generate excel report link

```shell
curl -X POST \
  https://beta.inkredo.in/api/v0/parser/excel/ \
  -H 'Content-Type: application/json' \
  -H 'access-id: your_access_id' \
  -H 'access-key: your_access_key' \
  -d '{
	"borrowerId":"5c6a5cbe8e4b510b60e7633a"
}'
```

> The above command returns JSON structured like this:

```json
{
    "success": true,
    "message": "Download link generated successfully",
    "downloadLink": "https://inkredo-reports.amazonaws.com/reprot.xlsx"
}
```

This endpoint provides a link to download the report in excel format. To download the excel file, you can visit the link returned in <code>downloadLink</code> of the response body.

### HTTP Request

`POST https://beta.inkredo.in/api/v0/parser/excel`

### Headers
Name | Value
---|---
Content-Type | application/json
access-id | your_access_id
access-key | your_access_key


### Body

Parameter | Required | Description
--------- | ------- | -----------
borrowerId | true | borrower ID

<aside class="notice">
The <code>downloadLink</code> will expire after 10 minutes
</aside>


## Extract PII

```shell
curl -X POST \
  https://beta.inkredo.in/api/v0/extract_pii/ \
  -H 'Content-Type: multipart/form-data' \
  -H 'access-id: your_access_id' \
  -H 'access-key: your_access_key' \
  -F 'pdf=@/path/to/file.pdf'
```

> The above command returns JSON structured like this:

```json
{
    "success": true,
    "data": {
        "account_number": "111111111111111111",
        "ifsc": "IFSC0123456",
        "pan": "ABCD1234F",
        "statement_period": {
            "from": "01/04/2018",
            "to": "30/04/2018"
        }
    },
}
```

This endpoint is for extracting PII from a bank statement. PII includes information like client's account number, IFSC, etc.

### HTTP Request

`POST https://beta.inkredo.in/api/v0/extract_pii`

### Headers
Name | Value
---|---
Content-Type | multipart/form-data
access-id | your_access_id
access-key | your_access_key


### Body

Parameter | Required | Description
--------- | ------- | -----------
pdf | true | PDF file object



