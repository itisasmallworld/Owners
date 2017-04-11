# Owners

## Function
- ユーザー管理機能
- プロジェクトの詳細ページ閲覧機能
- 商品購入機能

## DataBase Design

###Required Table
- persons table
- image table
- projects table
- person_projects table

### Required Columun

- #### persons table

|center align      |center align      |
|:----------------:|:----------------:|
|name              |t.string, null: false|
|mail              | t.string, null:false, unique: true|
|password          |t.string, null: false|
|project_id        |t.integer, null: false|

##### Association
has_many :images  
has_many :projects, through :person_projects


- #### projects table

|center align       |center align       |
|:-----------------:|:-----------------:|
|name               |t.string, null: false|
|price              |t.integer, null: false|
|quantity           |t.integer, null: false|
|address            |t.string, null: false|

##### Association
has_many :images  
has_many :persons, through :person_projects


- #### images table

|center align      |center align       |
|:----------------:|:-----------------:|
|image             |t.string, null:false|
|project_id        |t.integer, null: false|


##### Association
belongs_to :project  
belongs_to :person


- #### person_projects table

|center align       |center align         |
|:-----------------:|:-------------------:|
|person             |t.reference, index: true, foreign_key: true|
|projects           |t.reference, index: true, foreign_key: true|
|role               |t.string, null: false|

##### Association
belongs_to :person  
belongs_to :project
