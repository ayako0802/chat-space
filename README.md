# chat space

## DB設計

### usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_name|string|null: false|
|email|string|null: false, unique: true|
|password|string|null: false|

#### Association
- has_many :messages
- has_many :members

### groupsテーブル
|Column|Type|Options|
|------|----|-------|
|group_name|string|null: false|

#### Association
- has_many :members

### membersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

#### Association
- belongs_to :group
- belongs_to :user


### messagesテーブル
|Column|Type|Options|
|------|----|-------|
|timestamps|datetime|null: false|
|body|string||
|image|string||
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

#### Association
- belongs_to :user
