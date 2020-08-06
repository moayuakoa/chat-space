# README
グループを作って、チャットができるアプリケーション

### サインイン
[![Image from Gyazo](https://i.gyazo.com/42fc183d9c7a995589001d2317bc67d1.png)](https://gyazo.com/42fc183d9c7a995589001d2317bc67d1)

### ログイン
[![Image from Gyazo](https://i.gyazo.com/0411950678db89cd1a9b7afed81fc94f.png)](https://gyazo.com/0411950678db89cd1a9b7afed81fc94f)

### グループ編集画面
[![Image from Gyazo](https://i.gyazo.com/a50f823e4e58f908bd0aa31fd94950c5.gif)](https://gyazo.com/a50f823e4e58f908bd0aa31fd94950c5)

### メッセージ送信画面
[![Image from Gyazo](https://i.gyazo.com/44f3e4169f29bc6badd7592f14eca031.gif)](https://gyazo.com/44f3e4169f29bc6badd7592f14eca031)
## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false, index: true, unique: true|
|email|string|null: false, unique: true|
|password|string|null: false|

### Association
- has_many :groups_users
- has_many :groups, through: :groups_users
- has_many :messages

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false, index: true, unique: true|

### Association
- has_many :groups_users
- has_many :users, through: :groups_users
- has_many :messages

## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|content|string||
|image|string||
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user