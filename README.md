# Owners

## Function
- ユーザー管理機能
- プロジェクトの詳細ページ閲覧機能
- 商品購入機能
- (プロジェクトのレビュー機能)

## DataBase Design

###Required Table
- users table
- producers table
- projects table
- comments table

### Required Columun

#### users table

|center align      |center align      |
|:----------------:|:----------------:|
|name              |t.string, null: false|
|mail              | t.string, null:false, unique: true|
|password          |t.string, null: false|

##### Association
has_many :projects  
has_many :producer, through :user_producers


#### producers table

|center align      |center align       |
|:----------------:|:-----------------:|
|name              |t.string, null:false|
|address           |t.string, null: false|


##### Association
has_one :project  
has_many :users, through :user_producers

#### projects table

|center align       |center align       |
|:-----------------:|:-----------------:|
|name               |t.string, null: false|
|price              |t.integer, null: false|
|quantity           |t.integer, null: false|

##### Association
belongs_to :user  
belongs_to :producer

#### user_producers table

|center align       |center align         |
|:-----------------:|:-------------------:|
|user               |t.reference, index: true, foreign_key: true|
|group              |t.reference, index: true, foreign_key: true|

##### Association
belongs_to :user  
belongs_to :producer
