# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# テーブル設計

## items テーブル

| Column          | Type       | Options                        |
| --------------- | ---------- | ------------------------------ |
| name            | string     | null: false                    |
| shop            | references |                                |
| price           | integer    |                                |
| description     | text       |                                |
| category_id     | integer    |                                |

### Association

- belongs_to :shop

## shops テーブル

| Column          | Type    | Options     |
| --------------- | ------- | ----------- |
| name            | string  | null: false |

### Association

- has_many :items
- has_many :carts

## carts テーブル

| Column          | Type        | Options                        |
| --------------- | ----------- | ------------------------------ |
| shop            | references  | null: false, foreign_key: true |

### Association

- belongs_to :shop
- has_many :cart_items
- has_one :purchased

## purchased テーブル

| Column          | Type        | Options                        |
| --------------- | ----------- | ------------------------------ |
| cart_price      | integer     | null: false                    |
| cart            | references  | null: false, foreign_key: true |

### Association

- belongs_to :cart

## cart_items テーブル

| Column          | Type        | Options                        |
| --------------- | ----------- | ------------------------------ |
| quantity        | integer     |                                |
| cart            | references  | null: false, foreign_key: true |
| item            | references  | null: false, foreign_key: true |

### Association

- belongs_to :cart
- belongs_to :item