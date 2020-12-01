# テーブル設計

## users テーブル

| Column          | Type   | Options     |
| --------------- | ------ | ----------- |
| last_name       | string | null: false |
| first_name      | string | null: false |
| last_name_kana  | string | null: false |
| first_name_kana | string | null: false |
| postal_code     | string | null: false |
| prefecture_id   | integer | null: false |
| city            | string | null: false |
| house_number    | string | null: false |
| building_name   | string |  |
| phone           | string | null: false |
| email           | string | null: false |
| line            | string | null: false |
| birthday        | date   | null: false |
| password        | string | null: false |

### Association

- has_many :purchases
- has_one :counseling



## counselings テーブル

| Column          | Type    | Options     |
| --------------- | ------- | ----------- |
| stress_id       | integer | null: false |  <!-- ストレスyn -->
| stress_causes   | string  |  |  <!-- 原因 -->
| sleep_time      | integer |  |  <!-- 睡眠時間 -->
| medical_id      | integer | null: false |  <!-- 病歴yn -->
| disease_name    | string  |  |  <!-- 病名 -->
| disease_time    | date    |  |  <!-- 時期 -->
| outpatient_id   | integer | null: false |  <!-- 通院yn -->
| medicine_id     | integer | null: false |  <!-- 服薬yn -->
| medicine        | string  |  |  <!-- 薬 -->
| tooth_id        | integer | null: false |  <!-- 歯科矯正＆インプラントyn -->
| allergy_id      | integer | null: false |  <!-- アレルギーyn -->
| allergy         | string  |  |  <!-- アレルギー -->
| cigarette_id    | integer | null: false |  <!-- タバコyn -->
| liquor_id       | integer | null: false |  <!-- お酒yn -->
| esthetic_id     | integer | null: false |  <!-- マッサージやエステの経験yn -->
| trouble_id      | integer |  |  <!-- トラブルの有無yn -->
| pregnancy_id    | integer | null: false |  <!-- 妊娠授乳 -->
| pregnancy_week  | string  |  |  <!-- 妊娠週数 -->
| points          | string  |  |  <!-- 気になる点 -->

## Association

- belongs_to :user



## items テーブル

| Column                | Type   | Options     |
| --------------------- | ------ | ----------- |
| product               | string | null: false |  
| description           | text   | null: false |
| price                 | integer | null: false |
| user_id               | integer | null: false, foreign_key: true |

## Association

- has_one :purchase



# purchases テーブル

| Column  | Type   | Options     |
| ------- | ------ | ----------- |
| user_id | integer | null: false, foreign_key: true |
| item_id | integer | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item



## menus テーブル

| Column                | Type   | Options     |
| --------------------- | ------ | ----------- |
| course_id             | integer | null: false | 
| description           | text    | null: false |
| price                 | integer | null: false |
| user_id               | integer | null: false, foreign_key: true |

## Association

- has_one :reservation



# reservations テーブル

| Column  | Type   | Options     |
| ------- | ------ | ----------- |
| user_id | integer | null: false, foreign_key: true |
| menu_id | integer | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item