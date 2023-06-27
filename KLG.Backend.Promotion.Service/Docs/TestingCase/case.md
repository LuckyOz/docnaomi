# Implement Case Untuk Promo Engine

## Description
<p> Di bagian ini akan membahas mengenai case - case yang sudah di test beserta detail cara membuat, terdapat 2 service yang akan di test , yaitu find promo test dan validate promo test. di dalam service yang sudah di sebutkan nanti akan dibagi menjadi beberapa kelompok berikut list pengelompokan promo yang akan dilakukan testing : </p>

* Cart
    * Percent
    * Amount
* Item
    * Percent
    * Amount
    * Get Item (Buy X Gey Y) or (Buy X Get X)
    * Special Price
    * Bundle ?
* MOP

## Template Promo Detail

Untuk melakukan testing case terdapat template yang harus di set sebelumnya, template tersebut sesuai dengan keperluan data yang di butuhkan oleh engine dalam mengelola promo untuk melihat secara detail template : 

* [**Find Template**](Find/FindTemplate.md#)
* [**Validate Template**](Validate/ValidateTemplate.md#)

## Example Testing

### Find Promo

* Cart
    * Amount
        * [**0001. Promo Amount Require And Implement All Item Result And**](Find/0001.md#)

    * Percent
        * [**0002. Promo Percent Require And Implement All Item Result And**](Find/0002.md#)

* Item
    * Amount
        * [**0003. Promo Amount Require Method OR Result Custom Item Method And**](Find/0003.md#)
        * [**0012. Test**]()
    * Percent
        * [**0004. Promo Percent Require Method OR Result Custom Item Method OR**](Find/0004.md#)
    * Get Item (Buy x Get Y / Buy x Get x)
        * [**0005. Promo Item Require Method OR Result Custom Item Method And**](Find/0005.md#)
    * Special Price
        * [**0006. Item Promo SP Require Method OR Result CUSTOM Item Method And**](Find/0006.md#)
* MOP
    * [**0007. Promo Mop Di Gabungkan Dengan Promo Cart**](Find/0007.md#)

* Special Case
    * [**0011. Find Promo Bertingkat**]()

### Validate & Calculate Promo

* [**0008. Promo MOP Cart**](Validate/0008.md#)
* [**0009. Promo Class Item Custom Item OR**](Validate/0009.md#)
* [**0010. Promo Bertingkat**](Validate/0010.md#)
