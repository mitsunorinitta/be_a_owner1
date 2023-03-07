# README

# アプリケーション名
Be a Owner

# アプリケーション概要
自身の飼っているペットの体調管理を行うアプリです。

# アプリケーションを作成した背景
自身が飼っているペットの体調管理を簡単に行うことが出来ると良いと思い、<br>
作成しています。

以前動物病院にて、動物看護師として勤務していた際、<br>
・ペットへの薬の投与を忘れてしまうことがある。<br>
・適切な1日のフードの投与量が分かりづらく、<br>
　あげすぎで太らせてしまうことがある。<br>
といった声をよく聞いていた為、このアプリを開発しようと考えました。

# 洗い出した要件
[要件を定義したシート](https://docs.google.com/spreadsheets/d/15aOR0Ce3oJxpzlPL6dvtctVHeJraPuQGzCnsdktLYu4/edit#gid=1785908763)

# 実装予定の機能
・ユーザー管理機能<br>
・ペットの登録機能<br>
・フードの投与量の計算機能<br>
・ペットの体調管理機能<br>
・薬の投与タイミングなどのリマインド機能<br>

# 開発環境
Ruby/Ruby on Rails/MySQL/Github/AWS/Visual Studio Code/Render


# テーブル設計

## Usersテーブル
| Column             | Type   | Options                   |
| ------------------ | ------ | ------------------------- |
| nickname           | string | null: false               |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false               |

### Association
has_many :animals


## Animalsテーブル
| Column            | Type       | Options                        |
| ----------------- | ---------- | ------------------------------ |
| pet_type_id       | integer    | null: false                    |
| animal_name       | string     | null: false                    |
| breed             | string     |                                |
| animal_color      | string     |                                |
| animal_gender_id  | integer    |                                |
| birth_day         | date       |                                |
| user              | references | null: false, foreign_key: true |

### Association
belongs_to :user
has_many :health_management_dates


## Health_management_datesテーブル
| Column           | Type    | Options     |
| ---------------- | ------- | ----------- |
| record_date      | date    | null: false |
| body_weight      | integer |             |
| appetite_id      | integer |             |
| vigor_id         | integer |             |
| vomit_id         | integer |             |
| diarrhea_id      | integer |             |
| memo             | string  |             |

### Association
belongs_to :animal