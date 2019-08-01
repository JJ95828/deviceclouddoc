登录api：    http://47.107.69.207:9998/api/v1/login

返回参数： "token" 、 "isSuperUser"（1为超级管理员，2为管理处/供应商，3公司，4项目）

获取token后所有请求头部添加token

退出：http://47.107.69.207:9998/api/v1/logout

修改密码：http://47.107.69.207:9998/api/v1/resetPassword  
请求参数："password"   （用户登录后，个人中心的密码修改---password为新密码）

修改昵称和手机号码：http://47.107.69.207:9998/api/v1/resetNickNameAndPhoneNum  
请求参数："nickName"、"phoneNum"  （用户登录后，修改昵称，号码）

获取用户信息：http://47.107.69.207:9998/api/v1/getUserInfo  
返回参数：
|  参数   | 说明  |
|  ----  | ----  |
| name  | 名字 |
| nickName  | 昵称 |
| phoneNum  | 号码 |
| superCompanyName  | 超级（一级）公司 |
| isSuperUser  | 是否是管理员（1、超级，2、供应商/管理处，3、公司，4、项目） |
| avatarURL  | imgUrl |

### 代理商/管理处：

|  api   | 请求参数（data） | 返回参数 | header(头部) | 说明 |
|  ----  | ----  | ----  | ---- | ---- |
| api/v1/getAllAgents  | --- | agentID(管理处id)、agentName(名字)、remark(描述)、createdAt(时间) | token | 获取超级公司下的所有供应商/管理处 |
| api/v1/addAgent  | name(管理处名字)、remark(描述、说明) | success | token | 超级账号登录后，添加管理处 |
| api/v1/updateAgent  | id(管理处id)、name(管理处名字)、remark(描述、说明) | success | token | 超级账号登录后，更新管理处信息 |
| api/v1/deleteAgent  | id(管理处id)| success | token | 上传管理处id，删除该管理处/供应商 |
| api/v1/getAllAgentUsers  | ---| users{id(用户id)、name(用户名)、nickName(昵称)、phoneNumber(号码)} | token、agentid(管理处id) | 超级账号后进入管理处，获取管理处管理员用户 |
| api/v1/getNoAgentUser  | ---| users{id(用户id)、name(用户名)、nickName(昵称)、phoneNumber(号码)} | token、agentid(管理处id) | 超级账号后进入管理处，获取管理处 非管理员用户 |
| api/v1/addAgentUser  | ids(数组格式，可多选--用户的id) | success | token、agentid(管理处id) | 超级账号后进入管理处，添加管理处管理员 |
| api/v1/deletAgentUser  | ids(数组格式，可多选--用户的id) | success | token、agentid(管理处id) | 超级账号后进入管理处，取消管理处管理员 |

### company公司：

|  api   | 请求参数（data） | 返回参数 | header(头部) | 说明 |
|  ----  | ----  | ----  | ---- | ---- |
| api/v1/getAllCompanys | --- | companyID(管理处id)、companyName(名字)、remark(描述)、createdAt(时间) | token、agentid(管理处id) | 进入管理处下的所有公司 |
| api/v1/addCompany  | name(公司名字)、remark(描述、说明) | success | token、agentid(管理处id) | 管理处下添加公司 |
| api/v1/updateCompany  | id(公司id)、name(公司名字)、remark(描述、说明) | success | token、agentid(管理处id) | 管理处下修改公司信息 |
| api/v1/deleteCompany  | id(公司id)| success | token、agentid(管理处id) | 公司id，管理处下删除该公司 |
| api/v1/getAllCompanyUsers  | ---| users{id(用户id)、name(用户名)、nickName(昵称)、phoneNumber(号码)} | token、agentid(管理处id)、companyId(公司id) | 进入公司下，获取公司管理员用户 |
| api/v1/getNoCompanyUser  | ---| users{id(用户id)、name(用户名)、nickName(昵称)、phoneNumber(号码)} | token、agentid(管理处id)、companyId(公司id) | 进入公司，公司非管理员用户 |
| api/v1/addCompanyUser  | ids(数组格式，可多选--用户的id) | success | token、agentid(管理处id)、companyId(公司id) | 公司下，添加公司管理员 |
| api/v1/deletCompanyUser  | ids(数组格式，可多选--用户的id) | success | token、agentid(管理处id)、companyId(公司id) | 公司下，取消公司管理员 |