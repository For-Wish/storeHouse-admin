# storeHouse 数据库设计

## 1、用户表（userInfo：登录、注销等）

|      | 命名             | 注释               | 数据类型     | 是否为空 |
| ---- | ---------------- | :----------------- | ------------ | -------- |
| 1    | uid🔑             | 用户 id            | int(10)      | **否**   |
| 2    | account          | 昵称               | varchar(50)  | **否**   |
| 3    | password         | 密码               | varchar(50)  | **否**   |
| 4    | telephone_number | 电话号码           | varchar(20)  | 是       |
| 5    | avatar_address   | 头像地址           | varchar(100) | 是       |
| 6    | eamil            | 邮箱               | varchar(50)  | 是       |
| 7    | introduce        | 介绍               | varchar(50)  | 是       |
| 8    | create_time      | 注册时间           | datetime     | **否**   |
| 9    | topic_count      | 话题数目           | int(10)      | **否**   |
| 10   | comment_count    | 评论数目           | int(10)      | **否**   |
| 11   | nano_id          | nanoId唯一身份标识 | int(50)      | **否**   |
| 12   | url              | 网址               | varchar(50)  | 是       |
| 13   | user_state       | 用户状态           | int(2)       | **否**   |



## 2、评论表（comment：用户评论）

|      | 命名                    | 注释            | 数据类型    | 是否为空 |
| ---- | ----------------------- | :-------------- | ----------- | -------- |
| 1    | comment_id🔑             | 评论 id         | int(10)     | **否**   |
| 2    | content                 | 评论内容        | varchar(50) | **否**   |
| 3    | comment_uid (外键)      | 评论者 Id       | int(10)     | **否**   |
| 4    | comment_topic_id (外键) | 评论所属话题 id | int(10)     | **否**   |
| 5    | comment_time            | 评论时间        | datetime    | **否**   |
| 7    | comment_ip              | 网络地址        | varchar(50) | 是       |
| 8    | comment_equipment       | 持用设备        | varchar(50) | 是       |





## 3、贴子表 （topic：发贴、删帖等）

|      | 命名                    | 注释        | 数据类型    | 是否为空 |
| ---- | ----------------------- | :---------- | ----------- | -------- |
| 1    | topic_id🔑               | 贴子 id     | int(10)     | **否**   |
| 2    | title                   | 贴子标题    | varchar(50) | **否**   |
| 3    | topic_content           | 贴子内容    | longtext    | **否**   |
| 4    | comment_count           | 评论总数    | int(10)     | 是       |
| 5    | topic_time              | 发帖时间    | datetime    | 是       |
| 6    | topic_uid (外键)        | 创建者 id   | int(10)     | **否**   |
| 7    | topic_category_id(外键) | 所属板块 id | int(10)     | **否**   |
| 8    | topic_tag_id (外键)     | 所属标签 id | int(10)     | **否**   |
| 9    | browse_count            | 浏览量      | int(10)     | 是       |
| 10   | thumbs_up               | 点赞数目    | int(10)     | **否**   |



## 4、板块表 （ **category** ：大板块表）

|      | 命名           | 注释         | 数据类型     | 是否为空 |
| ---- | -------------- | :----------- | ------------ | -------- |
| 1    | category_id🔑   | 板块 id      | int(10)      | **否**   |
| 2    | category_title | 板块标题     | varchar(50)  | **否**   |
| 3    | topic_count    | 板块话题数   | int(10)      | 是       |
| 4    | comment_count  | 板块评论数   | int(10)      | 是       |
| 5    | description    | 板块描述内容 | varchar(200) | **否**   |
| 6    | category_logo  | 板块logo     | varchar(200) | **否**   |



## 5、标签表（tag：板块下的小分类）

|      | 命名                   | 注释            | 数据类型    | 是否为空 |
| ---- | ---------------------- | :-------------- | ----------- | -------- |
| 1    | tag_id🔑                | 标签 id         | int(10)     | **否**   |
| 2    | tag_name               | 标签名称        | varchar(50) | **否**   |
| 3    | topic_count            | 标签话题数      | int(10)     | 是       |
| 4    | tag_category_id (外键) | 标签所属板块 id | int(10)     | **否**   |



## 6、点赞表（thumbs：点赞表）

|      | 命名                  | 注释        | 数据类型 | 是否为空 |
| ---- | --------------------- | :---------- | -------- | -------- |
| 1    | thumbs_id🔑            | 标签 id     | int(10)  | **否**   |
| 2    | thumbs_uid (外键)     | 点赞者 id   | int(10)  | **否**   |
| 3    | thumbs_topicId (外键) | 点赞话题 id | int(10)  | **否**   |



## 7、通知表（notification：点赞或评论等等通知）

|      | 命名            | 注释          | 数据类型     | 是否为空 |
| ---- | --------------- | :------------ | ------------ | -------- |
| 1    | nid🔑            | 通知自增 id   | int(10)      | **否**   |
| 2    | action          | 通知操作      | varchar(100) | **否**   |
| 3    | subject_id      | 附带的主题 id | int(10)      | **否**   |
| 4    | user_Id (外键)  | 用户 id       | int(10)      | **否**   |
| 5    | from_uid (外键) | 发送通知者 id | int(10)      | **否**   |
| 6    | read_at         | 通知阅读时间  | datetime     | **否**   |



## 8、config 表（后台管理配置表）

|      | 命名             | 注释                     | 数据类型     | 是否为空 |
| ---- | ---------------- | :----------------------- | ------------ | -------- |
| 1    | cid🔑             | 标签 id                  | int(10)      | **否**   |
| 2    | smtp_eamil       | smtp 账户                | varchar(50)  | **否**   |
| 3    | smtp_pwd         | smtp 密码                | varchar(50)  | **否**   |
| 4    | baidu_app_key    | 百度文本识别的 appkey    | varchar(100) | 是       |
| 5    | baidu_secret_key | 百度文本识别的 secretkey | varchar(100) | 是       |
| 6    | geetest_id       | 极验Id                   | varchar(100) | 是       |
| 7    | geetest_key      | 极验Key                  | varchar(100) | 是       |



## 9、collection表（收藏表：收藏贴子）

|      | 命名                | 注释        | 数据类型 | 是否为空 |
| ---- | ------------------- | :---------- | -------- | -------- |
| 1    | collection_id🔑      | 收藏表 id   | int(10)  | **否**   |
| 2    | collection_uid      | 收藏者 id   | int(10)  | **否**   |
| 3    | collection_topic_id | 收藏贴子 id | int(10)  | **否**   |

