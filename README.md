# Owners

## Function
- ユーザー管理機能
- プロジェクトの詳細ページ閲覧機能
- 商品購入機能

## DataBase Design

### Required Table
- users table
- images table
- projects table
- rewards table
- supports table

### Required Columun

- #### users table

|__columun name__  |__type__          |__charactristics__  |
|:----------------:|:----------------:|:------------------:|
|name              |string            | null: false , unique: true       |
|mail              | string           |null:false, unique: true|
|password          |string            |null: false         |
|role              |string            |null: false         |

##### Association
has_many :projects  
has_many :rewards through :supports


- #### projects table

|__columun name__    |__type__           |__charactristics__|
|:------------------:|:-----------------:|:-----------------:|
|name                |string             |null: false|
|area                |string             |null: false|
|title               |string             |null: false|
|content             |text               |null: false|
|main_image          |string             |null: false|
|user_id             |integer            |null: false, foreign_key: true|

##### Association
has_many :images  
has_one  :reward  
belongs_to :user


- #### images table

|__columun name__  |__type__           |__charactristics__|
|:----------------:|:-----------------:|:----------------:|
|image             |string             |null:false|
|project_id        |integer            |null: false, foreign_key: true|

##### Association
belongs_to :project  


- #### rewards table

|__columun name__|__type__    |__charactristics__|
|:--------------:|:----------:|:----------------:|
|price           |integer     |null: false|
|quantity        |integer     |null: false|
|recruitment_capacity|integer |null: false|
|recruitment_term|integer     |null: false|
|name            |string      |null: false|
|project_id      |integer     |null: false, foreign_key: true|

##### Association
belongs_to :project  
has_many :users, through: supports

- #### supports table

|__columun name__   |__type__             |__charactristics__|
|:-----------------:|:-------------------:|:----------------:|
|user_id            |integer              |index: true, foreign_key: true|
|reward_id          |integer              |index :true, foreign_key: true|

##### Association
belongs_to :user  
belongs_to :reward

