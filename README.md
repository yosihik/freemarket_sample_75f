# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation
## usersテーブル

|Column|Type|Options|
|------|----|-------|
|family_name|string|null:false|
|first_name|string|null:false|
|family_name_kana|string|null:false|
|first_name_kana|string|null:false|
|nickname|string|null:false|
|introduction|text||
|email|string|null:false, unique: true, index:true|
|encrypted_password|string|null:false|
|birth_year|integer|null:false|
|birth_month|integer|null:false|
|birth_day|integer|null:false|


### Association
- has_many :items,dependent: :destroy
- has_many :credit_cards, dependent: :destroy
- has_one :deliver_address, dependent: :destroy
- belongs_to_active_hash :birth_dd
- belongs_to_active_hash :birth_mm
- belongs_to_active_hash :birth_yyyy



## itemsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null:false|
|price|integer|null:false|
|introduction|text|null:false|
|brand|string||
|size|integer||
|item_status|string|null:false|
|shipping_fee_burden|string|null:false|
|shipping_area_from|string|null:false|
|estimated_shipping_date|string|null:false|
|buyer_id|integer|null: false|
|user_id|references|null: false, foreign_key: true|
|category_id|references|null: false, foreign_key: true|


### Association
- has_many :item_images, dependent: :destroy
- belongs_to :user
- belongs_to :category

## deliver_addressesテーブル

|Column|Type|Options|
|------|----|-------|
|family_name|string|null:false|
|first_name|string|null:false|
|family_name_kana|string|null:false|
|first_name_kana|string|null:false|
|zip_code|string|null:false|
|city|string|null:false|
|address1|string|null:false|
|apartment-address|string||
|telephone|integer|unique: true|
|prefecture_id|integer|null:false|
|user_id|integer|null: false, unique: true|


### Association
- belongs_to :user
- Gem：jp_prefectureを使用して都道府県コードを取得

## credit_cardsテーブル

|Column|Type|Options|
|------|----|-------|
|payjp_id|string|null: false|
|user_id|references|null: false, foreign_key: true|


### Association
- belongs_to :user

## categoriesテーブル

|Column|Type|Options|
|------|----|-------|
|name|text|null:false|
|ancestry|string||


### Association
- has_many :items
- has_ancestry


## item_imagesテーブル

|Column|Type|Options|
|------|----|-------|
|src|string|null:false|
|item_id|references|null: false, foreign_key: true|


### Association
- mount_uploader :src, ImageUploader
- belongs_to :item

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...
