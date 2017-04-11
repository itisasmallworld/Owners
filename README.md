# Owners

## Function
- ユーザー管理機能
- プロジェクトの詳細ページ閲覧機能
- 商品購入機能

## DataBase Design

###Required Table
- people table
- images table
- projects table
- people_projects table

### Required Columun

- #### people table

|center align      |center align      |  center align      |
|:----------------:|:----------------:|:------------------:|
|__columun name__   |__type__         |__charactristics__  |
|name              |string            | null: false , unique: true       |
|mail              | string           |null:false, unique: true|
|password          |string            |null: false         |
|project_id        |integer           |null: false         |

##### Association
has_many :images  
has_many :projects, through :people_projects


- #### projects table

|center align       |center align       |center align       |
|:-----------------:|:-----------------:|:-----------------:|
|__columun name__    |__type__           |__charactristics__|
|name               |string|null: false|
|price              |integer|null: false|
|quantity           |integer|null: false|
|address            |string|null: false|

##### Association
has_many :images  
has_many :people, through :people_projects


- #### images table

|center align      |center align       |center align|
|:----------------:|:-----------------:|:----------:|
|__columun name__  |__type__           |__charactristics__|
|image             |string|null:false|
|project_id        |integer|null: false|


##### Association
belongs_to :project  
belongs_to :people


- #### people_projects table

|center align       |center align         |center align        |
|:-----------------:|:-------------------:|:------------------:|
|__columun name__   |__type__             |__charactristics__|
|people             |integer|index: true, foreign_key: true|
|projects           |integer|index: true, foreign_key: true|
|role               |string|null: false|

##### Association
belongs_to :people  
belongs_to :project
