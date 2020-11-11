## users テーブル

|       Column       |  Type   |   Options    |
|--------------------|---------|--------------|
| nickname           | string  | null: false  |
| encrypted_password | string  | null: false  |
| email              | string  | null: false  |
| first_name         | string  | null: false  |
| last_name          | string  | null: false  |
| first_yomigana     | string  | null: false  |
| last_yomigana      | string  | null: false  |
| birth_date         | date    | null: false  |

### Association
- has_many :items
- has_many :buy_records
- has_many :shipping_addresses

## items テーブル

|     Column      |   Type     |       Options     |
|-----------------|------------|-------------------|
| name            | string     | null: false       |
| comment         | text       | null: false       |
| category        | integer    | null: false       |
| status          | integer    | null: false       |
| user            | references | foreign_key: true |
| delivery_fee    | integer    | null: false       |
| shipment_source | integer    | null: false       |
| shipping_day    | integer    | null: false       |

### Association
- belongs_to :user
- has_one :buy_records
- belongs_to :shipping_address

## buy_records テーブル

|     Column      |   Type     |       Options     |
|-----------------|------------|-------------------|
| user            | references | foreign_key: true |
| item            | references | foreign_key: true |

### Association
- belongs_to :user
- belongs_to :item
- belongs_to :shipping_address

## shipping_addresses テーブル
|     Column      |   Type     |       Options     |
|-----------------|------------|-------------------|
| prefecture_id   | integer    | null: false       |
| city            | string     | null: false       |
| house_number    | references | foreign_key: true |
| building_name   | references | foreign_key: true |
| phone_number    | references | foreign_key: true |
| postal_cord     | references | foreign_key: true |

- belongs_to :user
- belongs_to :item
- belongs_to :shipping_address