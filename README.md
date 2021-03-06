# 智慧教育-网络学院示范应用


## 后端数据访问接口

### 主题状态

##### 1. **主题状态表**

列名 | 类型 | 长度
---|---|---
state_id | bigint(long) | 20
domain_id | bigint(long) | 20
states | varchar(string) | 255
user_id | bigint(long) | 20
created_time | datetime | 1
modified_time | datetime | 1


> 说明：

> - （1）	学习状态：0表示未学习，1表示正在学习，2表示已学习；

> - （2）	states（主题状态列表）形式：学习状态1，学习状态2，学习状态3，……

>       举例： 1， 0， 1， 2，……

---

##### 2.  **主题状态接口**  

> - （1）	/topicState/getByDomainIdAndUserId

> 查询主题状态，参数

long domainId | long userId
---|---
课程id | 用户id



> - （2）	/topicState/saveStateByDomainIdAndUserId

> 保存主题状态，参数

long domainId | String states | long userId
---|---|---
课程id | 主题状态列表 | 用户id
> - （3）	/topicState/saveStateByDomainNameAndUserId

> 保存主题状态，参数

long domainName | String states | long userId
---|---|---
课程名 | 主题状态列表 | 用户id

---

### 分面状态

##### 1. **分面状态表**

列名 | 类型 | 长度
---|---|---
state_id | bigint(long) | 20
domain_id | bigint(long) | 20
topic_id | bigint(long) | 20
states | varchar(string) | 255
user_id | bigint(long) | 20
created_time | datetime | 1
modified_time | datetime | 1

> 说明：

- （1）	学习状态：0表示未学习，1表示已在学习；

- （2）	states（分面状态列表）形式：学习状态1，学习状态2，学习状态3，……

>       举例： 1， 0， 1， 0，……

##### 2.  **分面状态接口**  

- （1）/facetState/getByDomainIdAndTopicIdAndUserId

> 查询分面状态，参数

long domainId | long userId | long topicId
---|--- |---
课程id | 用户id | 主题id
- （2）/facetState/saveStateByDomainIdAndTopicIdAndUserId

> 保存分面状态，参数

long domainId | long topicId | String states | long userId
---|---|---|---
课程id |主题id | 分面状态列表 | 用户id
- （3）/facetState/saveStateByDomainNameAndTopicNameAndUserId

> 保存分面状态，参数

string domainName | string topicName | String states | long userId
---|---|---|---
课程名 |主题名 | 分面状态列表 | 用户id
- （4）/facetState/saveStateByDomainIdAndUserId

> 保存分面状态，参数

long domainId | String states | long userId
---|---|---
课程id | 分面状态列表 | 用户id
- （5）/facetState/saveStateByDomainNameAndUserId

> 保存主题状态，参数

long domainName | String states | long userId
---|---|---
课程名 | 分面状态列表 | 用户id

***注***：states：分面状态的矩阵（行（主题）之间以分号隔开，行内以逗号隔开）
例如：0,0,1,0;0,0,1;1,1,0;1,0,1,1,1;……

---

### 推荐主题

##### 1. **推荐主题表**

列名 | 类型 | 长度
---|---|---
recommendation_id | bigint(long) | 20
domain_id | bigint(long) | 20
recommendation_topics | varchar(string) | 255
user_id | bigint(long) | 20
created_time | datetime | 1
modified_time | datetime | 1

> 说明：

- （1）recommendation_topics（推荐主题列表）形式：：推荐主题1 id，推荐主题2 id，推荐主题3 id；推荐主题3 id，推荐主题1 id，推荐主题4 id；……  
即，不同推荐方式之间以分号隔开，同一推荐方式内的主题id以逗号分隔开

##### 2.  **推荐主题接口**  

- （1）	recommendation/getByDomainIdAndUserId

> 查询推荐主题，参数

long domainId | long userId 
---|---
课程id | 用户id

- （2）	recommendation/saveRecommendationByDomainIdAndUserId

> 保存推荐主题，参数

long domainId | String recommendationTopics | long userId
---|---|---
课程id | 推荐主题列表 | 用户id
- （3）	recommendation/saveRecommendationByDomainNameAndUserId

> 保存推荐主题，参数

String domainName | String recommendationTopics | long userId
---|---|---
课程名 | 推荐主题列表 | 用户id

---

### 碎片评价

##### 1. **碎片评价表**

列名 | 类型 | 长度
---|---|---
evaluation_id | bigint(long) | 20
assemble_id | bigint(long) | 20
value | integer | 11
user_id | bigint(long) | 20
created_time | datetime | 1
modified_time | datetime | 1

> 说明：

- value 记录的是对应用户（user_id）在对应碎片（assemble_id）下的评价值，目前记录两个评价值（赞/踩），其中赞值为1，踩值为-1.

##### 2.  **碎片评价接口**  

- （1）evaluation/saveAssembleEvaluation

> 保存用户的碎片评价，参数

long assembleId | long userId | integer value
---|---|---
碎片id | 用户id | 评价值

---
