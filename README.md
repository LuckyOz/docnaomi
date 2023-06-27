# Promotion Engine

## Description
Promotion Engine merupaka suatu mesin pencari promo yang menggunakan salah satu library nuget milik microsoft yaitu [**Rules Engine**](https://microsoft.github.io/RulesEngine/#linkRulesEngine). Salah satu keunggulan di dalam Library ini yaitu sangat flexible dalam penambahan suatu rule atau penambahan promo baru sehingga tidak membutuhkan waktu lama untuk di jalankan di program. Library Nuget ini di install dan di jalankan  di dalam Framework Foundation dengan base NET 6.

## Struktur Library Rules Engine
Library ini memiliki struktur atau aturan tersendiri dalam penggunaanya, untuk aturanya data yang akan di jadikan rules engine dan di jalankan di dalam program harus dirubah atau di Convert ke dalam data JSON Array, untuk melihat strukturnya secara detail bisa klik [**disini**](#detail_struktur).

## ERD
Didalam struktur atau aturan JSON yang ada di dalam promotion engine terdapat beberapa data yang dibutuhkan, untuk data tersebut nantinya akan di simpan dan dimanipulate atau diolah oleh program, berikut tabel - tabel yang diperlukan untuk menjalankan Promotion Engine ini.

<img src="https://drive.google.com/uc?export=view&id=1zjr7SYpV2YFIRCt6NXIhFugHZsFQct4P" alt="Kawan Lama Group">

## Table List
1. [**PromoWorkflow**](KLG.Backend.Promotion.Service/Docs/TableDb/PromoWorkflow.md#).
2. [**PromoWorkflowExpression**](KLG.Backend.Promotion.Service/Docs/TableDb/PromoWorkflowExpression.md#).
3. [**PromoRule**](KLG.Backend.Promotion.Service/Docs/TableDb/PromoRule.md#).
4. [**PromoRuleVarible**](KLG.Backend.Promotion.Service/Docs/TableDb/PromoRuleVarible.md#).
5. [**PromoRuleExpression**](KLG.Backend.Promotion.Service/Docs/TableDb/PromoRuleExpressions.md#).
6. [**PromoRuleResult**](KLG.Backend.Promotion.Service/Docs/TableDb/PromoRuleResult.md#).

## Service Apps
* [**Find Promo**](KLG.Backend.Promotion.Service/Docs/ServicesApp/Find.md)
* [**Validate & Calculate Promo**](KLG.Backend.Promotion.Service/Docs/ServicesApp/Validate_Calculate.md)

## Testing Case
Pada bagian ini membahas mengenai testing case yang sudah di coba dan di implement ke dalam engine, untuk melihat lebih detail test apa saja yang sudah di implement bisa cek [**disini**](KLG.Backend.Promotion.Service/Docs/TestingCase/case.md#).



