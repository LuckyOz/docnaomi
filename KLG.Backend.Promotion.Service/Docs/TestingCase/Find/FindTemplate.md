
## Promo Detail
<table style="border:0px solid white;">
    <tr style="border: 0px;"> 
        <td style="border:0px;">1 .CompanyName</td>
        <td style="border:0px;">:</td>
        <td style="border:0px">CHATTIME</td>
    </tr>
        <tr style="border: 0px;"> 
        <td style="border:0px;">2. Code</td>
        <td style="border:0px;">:</td>
        <td style="border:0px">54ea8bee-0b64-11ee-be56-0242ac120002</td>
    </tr>
    <tr style="border: 0px;"> 
        <td style="border:0px;">3. Class</td>
        <td style="border:0px;">:</td>
        <td style="border:0px">Cart/Item/MOP</td>
    </tr>
    <tr style="border: 0px;"> 
        <td style="border:0px;">4. Name</td>
        <td style="border:0px;">:</td>
        <td style="border:0px">Promo New Year</td>
    </tr>
    <tr style="border: 0px;"> 
        <td style="border:0px;">5. ItemType</td>
        <td style="border:0px;">:</td>
        <td style="border:0px">ALL/CUSTOM</td>
    </tr>
    <tr style="border: 0px;"> 
        <td style="border:0px;">6. ResultType</td>
        <td style="border:0px;">:</td>
        <td style="border:0px">V1/V2</td>
    </tr>
    <tr style="border: 0px;"> 
        <td style="border:0px;">7. ActionType</td>
        <td style="border:0px;">:</td>
        <td style="border:0px">AMOUNT/PERCENT/ITEM/SP/BUNDLE</td>
    </tr>
    <tr style="border: 0px;"> 
        <td style="border:0px;">8. ActionValue</td>
        <td style="border:0px;">:</td>
        <td style="border:0px">5000/5%</td>
    </tr>
    <tr style="border: 0px;"> 
        <td style="border:0px;">9. MaxValue</td>
        <td style="border:0px;">:</td>
        <td style="border:0px">10000</td>
</table>

### Requirment Header
<table>
    <tr style="border: 0px;"> 
        <td style="border:0px;">Type</td>
        <td style="border:0px;">:</td>
        <td style="border:0px">AND / OR</td>
    </tr>
    <tr style="border: 0px;"> 
        <td style="border:0px;">DateStart</td>
        <td style="border:0px;">:</td>
        <td style="border:0px">25-12-2023 12:00:00</td>
    </tr>
    <tr style="border: 0px;"> 
        <td style="border:0px;">DateEnd</td>
        <td style="border:0px;">:</td>
        <td style="border:0px">25-12-2023 12:00:00</td>
    </tr>
    <tr style="border: 0px;"> 
        <td style="border:0px;">Grand Total Price</td>
        <td style="border:0px;">:</td>
        <td style="border:0px">>/=/< 200000</td>
    </tr>
    <tr style="border: 0px;"> 
        <td style="border:0px;">Grand Total Qty</td>
        <td style="border:0px;">:</td>
        <td style="border:0px">>/=/< 10</td>
    </tr>
</table>

### Requirment Detail

Zone
<table border>
    <tr>
        <td>No </td>
        <td>Zone</td>
    </tr>
    <tr>
        <td>1. </td>
        <td>zone001</td>
    </tr>
    <tr>
        <td>2. </td>
        <td>zone002</td>
    </tr>
<table>

Site
<table border>
    <tr>
        <td>No </td>
        <td>Site</td>
    </tr>
    <tr>
        <td>1. </td>
        <td>site001</td>
    </tr>
    <tr>
        <td>2. </td>
        <td>site002</td>
    </tr>
<table>

Item
<table border>
    <tr>
        <td>No </td>
        <td>Sku Code</td>
        <td>Qty</td>
    </tr>
    <tr>
        <td>1. </td>
        <td>milktea001</td>
        <td>2</td>
    </tr>
    <tr>
        <td>2. </td>
        <td>greendtea001</td>
        <td>2</td>
    </tr>
<table>

### Result
<table>
    <tr style="border: 0px;"> 
        <td style="border:0px;">Type</td>
        <td style="border:0px;">:</td>
        <td style="border:0px">OR</td>
    </tr>
</table>
<table border>
    <tr>
        <td>No </td>
        <td>Sku Code</td>
        <td>Value</td>
    </tr>
    <tr>
        <td>1. </td>
        <td>milktea001</td>
        <td>1000/10%/FREE/7000</td>
    </tr>
    <tr>
        <td>2. </td>
        <td>greendtea001</td>
        <td>1000/10%/FREE/7000</td>
    </tr>
<table>

## Implement to DB
```csharp
    new PromoWorkflow()
    {
        Id = "460d95b2-0b64-11ee-be56-0242ac120002",
        Name = "CHATIME",
        ActiveFlag = true,
        PromoWorkflowExpression = new List<PromoWorkflowExpression>()
        {//Var Total Price in Cart
            new PromoWorkflowExpression
            {
                Id = Guid.NewGuid().ToString(),
                Code = "varGlblTotalPrice",
                Name = "Total Price Item",
                Expression = "Convert.ToDecimal(paramsPromo.ItemProduct.Sum(y => Convert.ToDecimal(y.price) * Convert.ToDecimal(y.qty)))",
                ActiveFlag = true
            },
            //var Total Qty in Cart
            new PromoWorkflowExpression
            {
                Id = Guid.NewGuid().ToString(),
                Code = "varGlblTotalQty",
                Name = "Total Qty Item",
                Expression = "Convert.ToDecimal(paramsPromo.ItemProduct.Sum(y => Convert.ToDecimal(y.qty)))",
                ActiveFlag = true,
            },
            //var Date Convert From String
            new PromoWorkflowExpression
            {
                Id = Guid.NewGuid().ToString(),
                Code = "varGlblPrmDate",
                Name = "Params Date",
                Expression = "Convert.ToDateTime(paramsPromo.TransDate)",
                ActiveFlag = true,
            }
        },
        PromoRule = new List<PromoRule>
        {
            new PromoRule
            {
                Id = "54ea8bee-0b64-11ee-be56-0242ac120002",
                PromoWorkflowId = "460d95b2-0b64-11ee-be56-0242ac120002",
                Name = "Promo New Year",
                Cls = 1/2/3,
                Lvl = 1/2,
                ItemType = "ALL/CUSTOM",
                ResultType = "V1/V2",
                PromoActionType = "AMOUNT/PERCENT/ITEM/SP/BUNDLE",
                PromoActionValue = "5000/10%",
                MaxValue = "",
                StartDate = DateTime.UtcNow,
                EndDate = DateTime.UtcNow.AddMonths(1),
                ActiveFlag = true,
                PromoRuleVariable = new List<PromoRuleVariable>()
                {
                    new PromoRuleVariable
                    {
                        Id = Guid.NewGuid().ToString(),
                        Linenum = 1,
                        Code = "varLclStartDate",
                        Name = "Start Date",
                        ParamsExpression = "Convert.ToDateTime(\"25-12-2023 12:00:00\")",
                        ActiveFlag = true
                    },
                    new PromoRuleVariable
                    {
                        Id = Guid.NewGuid().ToString(),
                        Linenum = 2,
                        Code = "varLclEndDate",
                        Name = "End Date",
                        ParamsExpression = "Convert.ToDateTime(\"31-12-2024 00:00:00\")",
                        ActiveFlag = true
                    },
                    new PromoRuleVariable
                    {
                        Id = Guid.NewGuid().ToString(),
                        Linenum = 3,
                        Code = "varLclZone",
                        Name = "List Zone",
                        ParamsExpression = "new string[]{\"zone001\",\"zone002\"}",
                        ActiveFlag = true
                    },
                    new PromoRuleVariable
                    {
                        Id = Guid.NewGuid().ToString(),
                        Linenum = 4,
                        Code = "varLclSite",
                        Name = "List Site",
                        ParamsExpression = "new string[]{\"site001\",\"site002\"}",
                        ActiveFlag = true
                    },
                    new PromoRuleVariable
                    {
                        Id = Guid.NewGuid().ToString(),
                        Linenum = 5,
                        Code = "varLclItm",
                        Name = "List Item",
                        ParamsExpression = "new string[]{\"milktea001\",\"greentea001\"}",
                        ActiveFlag = true
                    }
                    
                },
                PromoRuleExpression = new List<PromoRuleExpression>()
                {
                    new PromoRuleExpression
                    {
                        Id = Guid.NewGuid().ToString(),
                        Linenum = 1,
                        Groupline = 0,
                        Code = "cekDateStart",
                        Name = "Cek Date Start",
                        ParamsExpression = "varGlblPrmDate >= varLclStartDate",
                        Linkexp = "AND/OR",
                        ActiveFlag = true
                    },
                    new PromoRuleExpression
                    {
                        Id = Guid.NewGuid().ToString(),
                        Linenum = 2,
                        Groupline = 0,
                        Code = "cekDateEnd",
                        Name = "Cek Date End",
                        ParamsExpression = "varLclEndDate >= varGlblPrmDate",
                        Linkexp = "AND/OR",
                        ActiveFlag = true
                    },
                    new PromoRuleExpression
                    {
                        Id = Guid.NewGuid().ToString(),
                        Linenum = 3,
                        Groupline = 0,
                        Code = "cekItem",
                        Name = "Cek Item Avail",
                        ParamsExpression = "paramsPromo.ItemProduct.Any(q => varLclItmPrm.Contains(q.SkuCode))",
                        Linkexp = "AND/OR",
                        ActiveFlag = true
                    },
                    new PromoRuleExpression
                    {
                        Id = Guid.NewGuid().ToString(),
                        Linenum = 4,
                        Groupline = 0,
                        Code = "cekQty",
                        Name = "Cek Qty Item",
                        ParamsExpression = "(paramsPromo.ItemProduct.Where(q => varLclItmPrm.Contains(q.SkuCode))).Sum(q => q.qty) >= 2",
                        Linkexp = "NULL",
                        ActiveFlag = true
                    }
                },
                PromoRuleResult = new List<PromoRuleResult>()
                {
                    new PromoRuleResult
                    {
                        Id = Guid.NewGuid().ToString(),
                        Linenum = 1,
                        Groupline = 0/1,
                        Linkrsl =  "AND/OR",
                        Item = "milktea001",
                        DscValue = "1000/10%/FREE/7000",
                        MaxValue = "",
                        ActiveFlag = true
                    },
                    new PromoRuleResult
                    {
                        Id = Guid.NewGuid().ToString(),
                        Linenum = 2,
                        Groupline = 0/2,
                        Linkrsl =  "",
                        Item = "1000/10%/FREE/7000",
                        DscValue = "2000",
                        MaxValue = "",
                        ActiveFlag = true
                    }
                }
            }
        }
    }   
```

## Request
```json
    {
  "trans_date": "25-12-2023 12:00:00",
  "item_product": [
    {
      "line_no": 1,
      "sku_code": "milktea001",
      "department": "",
      "commodity": "",
      "merchandise": "",
      "product_grouping": "milk",
      "qty": 10,
      "price": 10000
    },
    {
      "line_no": 2,
      "sku_code": "milktea005",
      "department": "",
      "commodity": "",
      "merchandise": "",
      "product_grouping": "milk",
      "qty": 5,
      "price": 8000
    }
  ],
  "zone": [
    "string"
  ],
  "site": [
    "string"
  ],
  "company_code": "460d95b2-0b64-11ee-be56-0242ac120002"
}
```

## Response
```json
{
    "data": [
        {
            "company_code": "460d95b2-0b64-11ee-be56-0242ac120002",
            "code": "72f58e00-0b68-11ee-be56-0242ac120002",
            "name": "Promo Milk Tea",
            "type": "AMOUNT",
            "type_result": "CUSTOM",
            "val_discount": "",
            "val_max_discount": "",
            "cls": 1,
            "lvl": 2,
            "promo_list_item": [
                {
                    "line_promo": 1,
                    "total_before": 110000.0,
                    "total_discount": 1000.0,
                    "total_after": 109000.0,
                    "rounding": 0,
                    "promo_list_item_detail": [
                        {
                            "line_no": 1,
                            "sku_code": "milktea001",
                            "val_discount": "1000",
                            "val_max_discount": "",
                            "price": 10000.0,
                            "qty": 1,
                            "total_price": 10000.0,
                            "total_discount": 1000.0,
                            "total_after": 9000.0
                        }
                    ]
                }
            ]
        },
        {
            "company_code": "460d95b2-0b64-11ee-be56-0242ac120002",
            "code": "72f58f90-0b68-11ee-be56-0242ac120002",
            "name": "Promo Green Tea",
            "type": "PERCENT",
            "type_result": "CUSTOM",
            "val_discount": "",
            "val_max_discount": "",
            "cls": 1,
            "lvl": 2,
            "promo_list_item": [
                {
                    "line_promo": 3,
                    "total_before": 110000.0,
                    "total_discount": 5000.0,
                    "total_after": 105000.0,
                    "rounding": 0,
                    "promo_list_item_detail": [
                        {
                            "line_no": 1,
                            "sku_code": "greentea001",
                            "val_discount": "5%",
                            "val_max_discount": "",
                            "price": 10000.0,
                            "qty": 10,
                            "total_price": 100000.0,
                            "total_discount": 5000.0,
                            "total_after": 95000.0
                        }
                    ]
                }
            ]
        },
        {
            "company_code": "460d95b2-0b64-11ee-be56-0242ac120002",
            "code": "72f5968e-0b68-11ee-be56-0242ac120002",
            "name": "Promo BCA",
            "type": "PERCENT",
            "type_result": "ALL",
            "val_discount": "10%",
            "val_max_discount": "",
            "cls": 3,
            "lvl": 2,
            "promo_list_item": [
                {
                    "line_promo": 1,
                    "total_before": 110000.0,
                    "total_discount": 11000.0,
                    "total_after": 99000.0,
                    "rounding": 0,
                    "promo_list_item_detail": [
                        {
                            "line_no": 1,
                            "sku_code": "greentea001",
                            "val_discount": "10%",
                            "val_max_discount": "",
                            "price": 10000.0,
                            "qty": 10,
                            "total_price": 100000.0,
                            "total_discount": 10000.0,
                            "total_after": 90000.0
                        },
                        {
                            "line_no": 1,
                            "sku_code": "milktea001",
                            "val_discount": "10%",
                            "val_max_discount": "",
                            "price": 10000.0,
                            "qty": 1,
                            "total_price": 10000.0,
                            "total_discount": 1000.0,
                            "total_after": 9000.0
                        }
                    ]
                }
            ]
        },
        {
            "company_code": "460d95b2-0b64-11ee-be56-0242ac120002",
            "code": "72f5981e-0b68-11ee-be56-0242ac120002",
            "name": "Promo OVO",
            "type": "PERCENT",
            "type_result": "ALL",
            "val_discount": "5%",
            "val_max_discount": "",
            "cls": 3,
            "lvl": 2,
            "promo_list_item": [
                {
                    "line_promo": 1,
                    "total_before": 110000.0,
                    "total_discount": 5500.0,
                    "total_after": 104500.0,
                    "rounding": 0,
                    "promo_list_item_detail": [
                        {
                            "line_no": 1,
                            "sku_code": "greentea001",
                            "val_discount": "5%",
                            "val_max_discount": "",
                            "price": 10000.0,
                            "qty": 10,
                            "total_price": 100000.0,
                            "total_discount": 5000.0,
                            "total_after": 95000.0
                        },
                        {
                            "line_no": 1,
                            "sku_code": "milktea001",
                            "val_discount": "5%",
                            "val_max_discount": "",
                            "price": 10000.0,
                            "qty": 1,
                            "total_price": 10000.0,
                            "total_discount": 500.0,
                            "total_after": 9500.0
                        }
                    ]
                }
            ]
        }
    ],
    "success": true,
    "message": "Success",
    "pages": 1,
    "total_pages": 1
}
```