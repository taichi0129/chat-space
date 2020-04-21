# DB設計

## users table
|Column|Type|Options|
|------|----|-------|
|e-mail|string|null: false, unique: true|
|password|integer|null: false|
|nickname|string|null: false, unique: true|
|group_id|integer|foreign_key: true|
### Association
- has_many :groups_users
- has_many :groups, through: groups_users
- has_many :messages

## messages table
|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|image|string|null: false|
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|
### Assosiation
- belongs_to :group
- belongs_to :user

## groups table
|Column|Type|Options|
|------|----|-------|
|group_name|string|null: false|
|user_id|integer|null: false, foreign_key: true|
### Assosiation
- has_many :groups_users
- has_many :users, through: groups_users
- has_many :messages

## groups_users table
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Assosiation
- belongs_to :user
- belongs_to :group