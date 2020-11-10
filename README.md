## users テーブル

|     Column     |  Type   |   Options    |
|----------------|---------|--------------|
| nickname       | string  | null: false  |
| password       | string  | null: false  |
| email          | string  | null: false  |
| first_name     | string  | null: false  |
| last_name      | string  | null: false  |
| first_yomigana | string  | null: false  |
| last_yomigana  | string  | null: false  |
| year           | integer | null: false  |
| month          | integer | null: false  |
| day            | integer | null: false  |

### Association
- has_many :items
- has_many :buy_records
- has_many :shipping_addresses

## items テーブル

|     Column      |   Type     |       Options     |
|-----------------|------------|-------------------|
| item_name       | string     | null: false       |
| item_comment    | text       | null: false       |
| image           |            | Active Storage    |
| category        | string     | null: false       |
| status          | string     | null: false       |
| user            | references | foreign_key: true |
| delivery_fee    | string     | null: false       |
| shipment_source | string     | null: false       |
| shipping_day    | string     | null: false       |

### Association
- belongs_to :user
- has_one :buy_records
- belongs_to :shipping_address

## buy_records テーブル

|     Column      |   Type     |       Options     |
|-----------------|------------|-------------------|
| user            | references | foreign_key: true |
| buy_year        | string     | null: false       |
| buy_month       | string     | null: false       |
| buy_day         | string     | null: false       |
| item            | references | foreign_key: true |

### Association
- belongs_to :user
- belongs_to :item
- belongs_to :shipping_address

## shipping_addresses テーブル
|     Column      |   Type     |       Options     |
|-----------------|------------|-------------------|
| prefectures     | string     | null: false       |
| municipalities  | string     | null: false       |
| address         | string     | null: false       |
| building_name   | string     |                   |
| phone_number    | string     | null: false       |
| postal_cord     | string     | null: false       |

- belongs_to :user
- belongs_to :item
- belongs_to :shipping_address