# Service Validate & Calculate Promo

# Description
<p>Pada bagian case ini akan menguji coba untuk proses validasi promo dan calculate promo itu sendiri</p>

# List Promo
List Promo yang akan di uji coba
- Promo A
- Promo B

# Request
```Json
{
  "trans_date": "string",
  "promoCode": [
    "string"
  ],
  "item_product": [
    {
      "line_no": 0,
      "sku_code": "string",
      "department": "string",
      "commodity": "string",
      "merchandise": "string",
      "product_grouping": "string",
      "qty": 0,
      "price": 0
    }
  ],
  "zone": [
    "string"
  ],
  "site": [
    "string"
  ],
  "mop": [
    {
      "name": "string",
      "amount": 0
    }
  ],
  "company_code": "string"
}
```

# Desc. Params Request
<table border>
    <tr>
        <td>No</td>
        <td>Name</td>
        <td>Tipe Data</td>
        <td>Desc</td>
    </tr>
    <tr>
        <td>1</td>
        <td>trans_date</td>
        <td>string_date</td>
        <td>Tanggal transaksi cart</td>
    </tr>
    <tr>
        <td>2</td>
        <td>promoCode</td>
        <td>list string</td>
        <td>List Promo Untuk Inject Promo</td>
    </tr>
        <tr>
        <td>3</td>
        <td>

[item_product](#item-product)</td>
        <td>list model</td>
        <td>List detail data item</td>
    </tr>
    <tr>
        <td>4</td>
        <td>zone</td>
        <td>list string</td>
        <td>List zone</td>
    </tr>
    <tr>
        <td>5</td>
        <td>site</td>
        <td>list string</td>
        <td>List site</td>
    </tr>
        <tr>
        <td>6</td>
        <td>
        
[mop](#mop)</td>
        <td>list model</td>
        <td>List mop</td>
    </tr>
    <tr>
        <td>7</td>
        <td>company_code</td>
        <td>string</td>
        <td>Uuid company workflow</td>
    </tr>
<table>

### Item Product
<table border>
    <tr>
        <td>No </td>
        <td>Name</td>
        <td>Tipe Data</td>
        <td>Desc</td>
    </tr>
    <tr>
        <td>1. </td>
        <td>line_no</td>
        <td>int</td>
        <td>Line number item</td>
    </tr>
    <tr>
        <td>2. </td>
        <td>sku_code</td>
        <td>string</td>
        <td>Kode item</td>
    </tr>
    <tr>
        <td>3. </td>
        <td>department</td>
        <td>string</td>
        <td>Department item</td>
    </tr>
    <tr>
        <td>4. </td>
        <td>commodity</td>
        <td>string</td>
        <td>Commodity item</td>
    </tr>
    <tr>
        <td>5. </td>
        <td>merchandise</td>
        <td>string</td>
        <td>Merchandise item</td>
    </tr>
    <tr>
        <td>6. </td>
        <td>product_grouping</td>
        <td>string</td>
        <td>Grouping item</td>
    </tr>
    <tr>
        <td>7. </td>
        <td>qty</td>
        <td>decimal</td>
        <td>Qty item</td>
    </tr>
    <tr>
        <td>8. </td>
        <td>price</td>
        <td>decimal</td>
        <td>Harga base item</td>
    </tr>
<table>

### MOP
<table border>
    <tr>
        <td>No</td>
        <td>Name</td>
        <td>Tipe Data</td>
        <td>Desc</td>
    </tr>
    <tr>
        <td>1</td>
        <td>name</td>
        <td>string</td>
        <td>Nama MOP</td>
    </tr>
    <tr>
        <td>2</td>
        <td>amount</td>
        <td>decimal</td>
        <td>Total Pembayaran MOP</td>
    </tr>
</table>

# Response
```json
{
  "data": {
    "trans_date": "string",
    "zone": [
      "string"
    ],
    "site": [
      "string"
    ],
    "company_code": "string",
    "total_before": 0,
    "total_discount": 0,
    "total_after": 0,
    "item_product": [
      {
        "line_no": 0,
        "sku_code": "string",
        "product_grouping": "string",
        "qty": 0,
        "price": 0,
        "total_before": 0,
        "total_discount": 0,
        "total_after": 0,
        "promo_product": [
          {
            "code": "string",
            "name": "string",
            "line_promo": 0,
            "cls": 0,
            "lv": 0,
            "type": "string",
            "type_result": "string",
            "value": "string",
            "value_max": "string",
            "value_price": 0
          }
        ]
      }
    ]
  },
  "success": true,
  "message": "string",
  "pages": 0,
  "total_pages": 0
}
```
# Desc. Response
<table border>
    <tr>
        <td>No</td>
        <td>Name</td>
        <td>Tipe Data</td>
        <td>Desc</td>
    </tr>
    <tr>
        <td>1</td>
        <td>trans_date</td>
        <td>string date</td>
        <td>tanggal transaksi</td>
    </tr>
    <tr>
        <td>2</td>
        <td>zone</td>
        <td>list string</td>
        <td>list zone</td>
    </tr>
    <tr>
        <td>3</td>
        <td>site</td>
        <td>list string</td>
        <td>list site</td>
    </tr>
    <tr>
        <td>4</td>
        <td>company_code</td>
        <td>string</td>
        <td>kode company</td>
    </tr>
    <tr>
        <td>5</td>
        <td>total_before</td>
        <td>decimal</td>
        <td>total harga yang belum kena promo</td>
    </tr>
    <tr>
        <td>6</td>
        <td>total_discount</td>
        <td>decimal</td>
        <td>total promo</td>
    </tr>
    <tr>
        <td>7</td>
        <td>total_after</td>
        <td>decimal</td>
        <td>total harga yang sudah di kurangi promo</td>
    </tr>
    <tr>
        <td>8</td>
        <td>

[item_product](#item-product)</td>
        <td>list model</td>
        <td>list model detail item dan promo</td>
    </tr>
        <tr>
        <td>9</td>
        <td>success</td>
        <td>bool</td>
        <td>status api call</td>
    </tr>
    <tr>
        <td>10</td>
        <td>message</td>
        <td>string</td>
        <td>message result api</td>
    </tr>
    <tr>
        <td>11</td>
        <td>pages</td>
        <td>string</td>
        <td>halaman api</td>
    </tr>
    <tr>
        <td>12</td>
        <td>total_pages</td>
        <td>int</td>
        <td>total halaman api</td>
    </tr>
</table>

# Item Product

<table border>
    <tr>
        <td>No</td>
        <td>Name</td>
        <td>Tipe Data</td>
        <td>Desc</td>
    </tr>
    <tr>
        <td>1</td>
        <td>line_no</td>
        <td>int</td>
        <td>Line Number Item</td>
    </tr>
    <tr>
        <td>2</td>
        <td>sku_code</td>
        <td>string</td>
        <td>Kode item</td>
    </tr>
    <tr>
        <td>3</td>
        <td>product_grouping</td>
        <td>string</td>
        <td>Group item</td>
    </tr>
    <tr>
        <td>4</td>
        <td>qty</td>
        <td>double</td>
        <td>Quantity item</td>
    </tr>
    <tr>
        <td>5</td>
        <td>price</td>
        <td>decimal</td>
        <td>Harga satuan item</td>
    </tr>
    <tr>
        <td>6</td>
        <td>total_before</td>
        <td>decimal</td>
        <td>Total harga yang belum di kurangi promo di tiap item</td>
    </tr>
    <tr>
        <td>7</td>
        <td>total_discount</td>
        <td>decimal</td>
        <td>Total harga promo yang di dapatkan di tiap item</td>
    </tr>
    <tr>
        <td>8</td>
        <td>total_after</td>
        <td>decimal</td>
        <td>Total harga yang sudah di kurangi harga promo di tiap item</td>
    </tr>
    <tr>
        <td>9</td>
        <td>

[promo_product](#promo-product)</td>
        <td>list model</td>
        <td>Model data detail promom</td>
    </tr>
</table>

# Promo Product

<table border>
    <tr>
        <td>No</td>
        <td>Name</td>
        <td>Tipe Data</td>
        <td>Desc</td>
    </tr>
    <tr>
        <td>1</td>
        <td>code</td>
        <td>string</td>
        <td>Kode promo</td>
    </tr>
    <tr>
        <td>2</td>
        <td>name</td>
        <td>string</td>
        <td>Nama promo</td>
    </tr>
    <tr>
        <td>3</td>
        <td>line_promo</td>
        <td>int</td>
        <td>Line number kombinasi promo</td>
    </tr>
    <tr>
        <td>4</td>
        <td>cls</td>
        <td>int</td>
        <td>Tipe promo Cart/Item/Mop</td>
    </tr>
    <tr>
        <td>5</td>
        <td>lv</td>
        <td>int</td>
        <td>Level urutan eksekusi di dalam class</td>
    </tr>
    <tr>
        <td>6</td>
        <td>type</td>
        <td>string</td>
        <td>Tipe promo</td>
    </tr>
    <tr>
        <td>7</td>
        <td>type_result</td>
        <td>string</td>
        <td>Implementasi ke semua item atau custom item</td>
    </tr>
    <tr>
        <td>8</td>
        <td>value</td>
        <td>string</td>
        <td>Value promo</td>
    </tr>
    <tr>
        <td>9</td>
        <td>value_max</td>
        <td>string</td>
        <td>Value promo maximum</td>
    </tr>
    <tr>
        <td>10</td>
        <td>value_price</td>
        <td>decimal</td>
        <td>Price promo yang di dapatkan</td>
    </tr>
</table>