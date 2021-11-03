# DB 設計

## users table

| Column             | Type        | Options                      |
|--------------------|-------------|------------------------------|
| id                 | string      | null: false                  |
| encrypted_password | string      | null: false                  |
| last_name          | string      | null: false                  |
| first_name         | string      | null: false                  |
| birth              | date        | null: false                  |

### Association

* has_one :reservation
* has_many :windows

## reservations table

| Column           | Type        | Options                         |
|------------------|-------------|---------------------------------|
| reservation_time | datetime    | null: false                     |
| ontime           | timestamp   | null: false                     |
| user             | references  | null: false,foreign_key: true   |

### Association

- belongs_to :user
- has_one :window

## windows table

| Column      | Type         | Options                          |
|-------------|--------------|----------------------------------|
| user        | references   | null: false,foreign_key: true    |
| reservation        | references   | null: false,foreign_key: true    |

### Association

- belongs_to :user
- has_many   :reservations
