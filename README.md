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
- has_many :groups

### groupsテーブル
|Column|Type|Options|
|------|----|-------|
|group_name|string|null: false|
|master_user_id|integer|null: false, foreign_key: true|

#### Association
- has_many :members
- belongs_to :user


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
