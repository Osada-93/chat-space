# DB design

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|integer|null: false, unique: true|
|password|string|null: false|
|email|text|null: false, unique: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- has_many :posts
- has_many :users_groups
- has_many :groups through :users_groups


## postsテーブル

|Column|Type|Options|
|------|----|-------|
|body|text|-------|
|image|text|-------|
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group


## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|user_id|integer|null: false, foreign_key: true|

### Association
- has_many :posts
- has_many :users_groups
- has_many :users through :users_groups


## users_groupsテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group