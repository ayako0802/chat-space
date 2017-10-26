# chat space

## DB設計

### usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|email|string|null: false, unique: true|
|password|string|null: false|

#### Association
- has_many :messages
- has_many :members
- has_many :groups, through: :members


### groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|master_user_id|integer|null: false, foreign_key: true|

#### Association
- has_many :users
- has_many :members
- has_many :users, through: :members


### membersテーブル
userとgroupの中間テーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

#### Association
- belongs_to :user
- belongs_to :group


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
- belongs_to :group