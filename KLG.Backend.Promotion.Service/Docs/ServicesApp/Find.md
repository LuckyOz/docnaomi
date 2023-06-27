# Service Find Promo

## Description
<p> Endpoint find digunakan untuk melakukan pencarian promo yang sesuai dengan cart yang dikirim melalui params json dan promo yang sudah di daftarkan di db. </p>

## Params Request Json
```json
{
  "trans_date": "string",
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
  "company_code": "string"
}
```

## Desc. Params Request
<table border>
    <tr>
        <td>No </td>
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
        <td>
        
[item_product](#item-product)</td>
        <td>list_item_product</td>
        <td>List detail data item</td>
    </tr>
    <tr>
        <td>3</td>
        <td>zone</td>
        <td>list_string</td>
        <td>List zone</td>
    </tr>
    <tr>
        <td>4</td>
        <td>site</td>
        <td>list_string</td>
        <td>List site</td>
    </tr>
    <tr>
        <td>5</td>
        <td>company_code</td>
        <td>string</td>
        <td>Uuid company workflow</td>
    </tr>
<table>

### Item Product
<p>Model yang digunakan untuk menyimpan detail </p>
<table border>
    <tr>
        <td>No </td>
        <td>Name</td>
        <td>Tipe Data</td>
        <td>Desc</td>
    </tr>
    <tr>
        <td>1</td>
        <td>line_no</td>
        <td>int</td>
        <td>Line number item</td>
    </tr>
    <tr>
        <td>2</td>
        <td>sku_code</td>
        <td>string</td>
        <td>Kode item</td>
    </tr>
    <tr>
        <td>3</td>
        <td>department</td>
        <td>string</td>
        <td>Department item</td>
    </tr>
    <tr>
        <td>4</td>
        <td>commodity</td>
        <td>string</td>
        <td>Commodity item</td>
    </tr>
    <tr>
        <td>5</td>
        <td>merchandise</td>
        <td>string</td>
        <td>Merchandise item</td>
    </tr>
    <tr>
        <td>6</td>
        <td>product_grouping</td>
        <td>string</td>
        <td>Grouping item</td>
    </tr>
    <tr>
        <td>7</td>
        <td>qty</td>
        <td>decimal</td>
        <td>Qty item</td>
    </tr>
    <tr>
        <td>8</td>
        <td>price</td>
        <td>decimal</td>
        <td>Harga base item</td>
    </tr>
<table>

## Response Json
```json
{
  "data": [
    {
      "company_code": "string",
      "code": "string",
      "name": "string",
      "type": "string",
      "type_result": "string",
      "val_discount": "string",
      "val_max_discount": "string",
      "cls": 0,
      "lvl": 0,
      "promo_list_item": [
        {
          "line_promo": 0,
          "total_before": 0,
          "total_discount": 0,
          "total_after": 0,
          "rounding": 0,
          "promo_list_item_detail": [
            {
              "line_no": 0,
              "sku_code": "string",
              "val_discount": "string",
              "val_max_discount": "string",
              "price": 0,
              "qty": 0,
              "total_price": 0,
              "total_discount": 0,
              "total_after": 0
            }
          ]
        }
      ]
    }
  ],
  "success": true,
  "message": "string",
  "pages": 0,
  "total_pages": 0
}
```

## Desc. Response
<table border>
    <tr>
        <td>No </td>
        <td>Name</td>
        <td>Tipe Data</td>
        <td>Desc</td>
    </tr>
    <tr>
        <td>1. </td>
        <td>company_code</td>
        <td>string</td>
        <td>Code uuid company</td>
    </tr>
    <tr>
        <td>2. </td>
        <td>code</td>
        <td>string</td>
        <td>Code uuid promo</td>
    </tr>
    <tr>
        <td>3. </td>
        <td>name</td>
        <td>string</td>
        <td>Nama promo</td>
    </tr>
    <tr>
        <td>4. </td>
        <td>type</td>
        <td>string</td>
        <td>Tipe promo (Percent/amount/Item/SP/Bundle)</td>
    </tr>
    <tr>
        <td>5. </td>
        <td>type_result</td>
        <td>string</td>
        <td>Jenis result dari promo (ALL/Custom)</td>
    </tr>
    <tr>
        <td>6. </td>
        <td>val_discount</td>
        <td>string</td>
        <td>Value discount untuk type_result = ALL</td>
    </tr>
    <tr>
        <td>7. </td>
        <td>val_max_discount</td>
        <td>string</td>
        <td>Value max discount (Percent) untuk type_result = ALL</td>
    </tr>
    <tr>
        <td>8. </td>
        <td>cls</td>
        <td>string</td>
        <td>Class Promo , 1(Item), 2(Cart), 3(MOP)</td>
    </tr>
    <tr>
        <td>9. </td>
        <td>lvl</td>
        <td>string</td>
        <td>Level Exec Promo, 1(Get Item), 2(Selain Get Item)</td>
    </tr>
    <tr>
        <td>10. </td>
        <td>
        
[promo_list_item](#promo-list-item)
        </td>
        <td>list_model</td>
        <td>list model promo item</td>
    </tr>
    <tr>
        <td>11. </td>
        <td>success</td>
        <td>bool</td>
        <td>status api call</td>
    </tr>
    <tr>
        <td>5. </td>
        <td>message</td>
        <td>string</td>
        <td>message result api</td>
    </tr>
    <tr>
        <td>5. </td>
        <td>pages</td>
        <td>string</td>
        <td>halaman api</td>
    </tr>
    <tr>
        <td>5. </td>
        <td>total_pages</td>
        <td>int</td>
        <td>total halaman api</td>
    </tr>
<table>

### Promo List Item

<p>Model promo_list_item merupakan sebuah model json yang menyimpan data kombinasi item dari hasil promo yang ada, untuk result tipe AND hanya terdapat 1 kombinasi, namun jika tipe or maka akan keluar beberapa tipe kombinasi yang ada</P>

<table border>
    <tr>
        <td>No</td>
        <td>Name</td>
        <td>Tipe Data</td>
        <td>Desc</td>
    </tr>
    <tr>
        <td>1</td>
        <td>line_promo</td>
        <td>int</td>
        <td>line untuk kombinasi promo</td>
    </tr>
    <tr>
        <td>2</td>
        <td>total_before</td>
        <td>decimal</td>
        <td>total harga cart sebelum di potong promo</td>
    </tr>
    <tr>
        <td>3</td>
        <td>total_discount</td>
        <td>decimal</td>
        <td>total promo yang digunakan</td>
    </tr>
    <tr>
        <td>4</td>
        <td>total_after</td>
        <td>decimal</td>
        <td>total harga cart dikurangi dengan total promo/discount</td>
    </tr>
    <tr>
        <td>5</td>
        <td>rounding</td>
        <td>decimal</td>
        <td>sisa dari promo, terutama dari promo amount yang di apply ke beberapa item atau ke all item</td>
    </tr>
    <tr>
        <td>6</td>
        <td>

[promo_list_item_detail](#promo-list-item-detail)</td>
        <td>list_model</td>
        <td>list detail item ketika di gunakan promo</td>
    </tr>
</table>

### Promo List Item Detail
<p>Merupkan model yang menyimpan data item yang terkena promo di kombinasi promo tersebut</p>

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
        <td>Line number untuk item</td>
    </tr>
    <tr>
        <td>2</td>
        <td>sku_code</td>
        <td>string</td>
        <td>Kode item</td>
    </tr>
    <tr>
        <td>3</td>
        <td>val_discount</td>
        <td>string</td>
        <td>Value promo</td>
    </tr>
    <tr>
        <td>4</td>
        <td>val_max_discount</td>
        <td>string</td>
        <td>value max discount</td>
    </tr>
    <tr>
        <td>5</td>
        <td>price</td>
        <td>decimal</td>
        <td>Harga base item</td>
    </tr>
    <tr>
        <td>6</td>
        <td>qty</td>
        <td>double</td>
        <td>Quantity item</td>
    </tr>
    <tr>
        <td>7</td>
        <td>total_price</td>
        <td>decimal</td>
        <td>Total harga item sebelum kena discount dan sudah dikalikan dengna qty</td>
    </tr>
    <tr>
        <td>8</td>
        <td>total_discount</td>
        <td>decimal</td>
        <td>Total promo yang di implement ke item</td>
    </tr>
    <tr>
        <td>9</td>
        <td>total_after</td>
        <td>decimal</td>
        <td>Total harga yang sudah termasuk dengan promo</td>
    </tr>
</table>