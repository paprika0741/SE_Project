# 详细设计说明书

## 1 引言

### 1.1 编写目的

 本详细设计说明书是针对表情包论坛项目编写。目的是对该项目进行详细设计，在概要设计的基础上进一步明确系统结构，详细地介绍系统的各个模块，为进行后面的实现和测试做准备。

本详细设计说明书的预期读者为本项目小组的成员以及对该项目感兴趣，在以后想对系统进行拓展和维护的人员。

### 1.2 背景 

1. 待开发项目的名称：表情包论坛
2. 本项目的任务提出者： 欧阳蓓，杨可，吴冠谦
3. 本项目任务开发者： 欧阳蓓，杨可，吴冠谦
4. 本项目用户：任何可访问的网络使用者

### 1.3 定义

查询：对数据库的一种操作，用于搜索数据信息。

插入：对数据库的一种操作，用于将数据存入数据库中。

更新：对数据库的一种操作，用于更改数据库中的数据信息。

HTTP: 超文本传输协议（Hyper Text Transfer Protocol，HTTP）是一个简单的请求-响应协议，它通常运行在[TCP](https://baike.baidu.com/item/TCP/33012)之上。它指定了客户端可能发送给服务器什么样的消息以及得到什么样的响应。

UML ：统一建模语言(Unified Modeling Language，UML)是一种为面向对象系统的产品进行说明、可视化和编制文档的一种标准语言，是非专利的第三代建模和规约语言。

REST：Representational State Transfer的缩写， 使用URL定位资源，用HTTP动词（GET,POST,DELETE,DETC）描述操作。用来规范客户端如何在HTTP 层与 API 提供方进行数据交互 

### 1.4 参考资料

1. 《GB/T 8567-2006 计算机软件文档编制规范》
2. 《GB/T 8567-1988 计算机软件产品开发文件编制指南》

## 2 程序系统的组织结构 

前台分为 个人信息管理模块，表情包分类展示模块，分享管理模块，收藏管理模块，评论管理模块

后台分为用户管理模块，推荐表情包模块

个人信息管理模块：在用户登录的情况下，用户可以点击“修改个人资料”，进入用户修改个人资料功能页面。

表情包分类展示模块：主页可根据用户输入不同分类展示不同表情包。

分享管理模块：在用户登录的情况下，用户可以在主页点击“分享表情包”进入表情包分享服务。对于发布新的表情包，用户可以选择上传图片，图片从用户本地，上传到网站服务器上；选择表情包的类别。用户可以修改或者删除自己发表的表情包，也可以点赞或者取消点赞其他用户的分享。

收藏管理模块：在用户登录的情况下，用户可以收藏或取消网站中所有的表情包。

评论管理模块：在用户的登录状态下，用户可以评论自己或者其他用户发表的分享，也可以修改或删除评论。用户可以点赞或者取消点赞其他用户评论。

用户管理模块：用户可以注册，登录账号。

推荐表情包模块：统计用户信息、进行个性化推荐

  <img src="https://pig-1307013046.cos.ap-nanjing.myqcloud.com/PigCo/acabb5d3-44b0-4d22-a6c5-6cf22bda3af5.svg" alt="acabb5d3-44b0-4d22-a6c5-6cf22bda3af5" style="zoom:67%;" />

 

###  

### 2.1 **模型（即数据表）：**

| 用户表       | Users        | 记录用户信息             |
| ------------ | ------------ | ------------------------ |
| 密保问题表   | *Securities* | 记录用户密保问题以及答案 |
| 收藏         | Stickers     | 记录表情包信息           |
| 收藏**表**   | Collections  | 记录用户收藏             |
| 类别表       | Categories   | 记录表情包分类           |
| 分享表       | Shares       | 记录用户分享             |
| 评论表       | Comments     | 记录用户评论             |
| 表情包点赞表 | StickerLikes | 记录表情包点赞           |
| 评论点赞表   | Commentlikes | 记录评论点赞             |

![img](https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=MTkxZGJhZTllMjM0YjgxNTQ2YjA3YzM3OTUzZGMyNDRfQW9YMWJVa3h5Rkp6S2taemtUZkJ1QVZvalpxck1Kb0lfVG9rZW46Ym94Y25UWVVnUUp4ZndabFRxeTRoZWxJMkFoXzE2NTMwMzY2ODI6MTY1MzA0MDI4Ml9WNA)

### 2.2 **视图：**

| 页面           | 描述                                                         |
| -------------- | ------------------------------------------------------------ |
| 注册页面       | 显示用户名，用户密码，密保问题，验证手机号，邮箱账号的输入框。对于输入的合法性返回提示信息 |
| 登录页面       | 显示用户名，密码的输入框。输入的合法性返回提示信息。提供跳转到修改密码的链接 |
| 修改密码页面   | 显示密保问题，提示用用户输入密保问题答案，和两次输入新密码。对于输入的合法性返回提示信息 |
| 用户资料页面   | 显示用户的资料信息：用户名，用户头像，喜好                   |
| 表情包主页     | 显示表情包及其描述。根据用户的喜好以及当前热点推荐。表情包下方显示点赞，收藏，评论数目 |
| 表情包分类页面 | 输入框供用户输入表情包类别，显示分类结果。表情包下方显示点赞，收藏，评论数目。 |
| 新建分享页面   | 显示上传图片，输入描述，分类信息的输入框                     |
| 收藏页面       | 显示用户的收藏图片                                           |
| 评论页面       | 显示用户分享的评论内容以及评论点赞信息                       |
| 新建评论页面   | 显示评论输入框以及输入完成的确认建。对于输入的合法性返回提示信息 |



## 3 个人信息管理模块 设计说明 

### 3.1 程序描述

在用户登录的情况下，用户可以点击“修改个人资料”，进入用户修改个人资料功能页面。

### 3.2 功能

功能范例

| 功能     | 格式/请求 | 功能描述                                                     |
| -------- | --------- | ------------------------------------------------------------ |
| 注册     | json/POST | 注册账户                                                     |
| 登录     | json/POST | 登录账户，数据库验证                                         |
| 登出     | json/POST | 关闭session                                                  |
| 重置密码 | json/POST | 回答密保问题正确后才能重置密码, 在重置密码时重复输入两次新密码保证相同后才能往下执行 |
| 上传头像 | json/POST | 上传图片文件                                                 |

### 3.3 性能

| 运行     | 模块组合                                   | 响应时间(ms)               |
| -------- | ------------------------------------------ | -------------------------- |
| 注册     | 个人信息管理模块、数据库模块、用户管理模块 | 1000ms                     |
| 登录     | 个人信息管理模块、数据库模块               | 100ms                      |
| 登出     | 个人信息管理模块                           | 10ms                       |
| 重置密码 | 个人信息管理模块、数据库模块、用户管理模块 | 100ms                      |
| 上传头像 | 个人信息管理模块、数据库模块               | 具体网络速度和图片大小有关 |

### 3.4 输入项

#### 3.4.1 用户注册

```Go
type RegisterRequest struct {
   Username string `json:"username"`
   Password string `json:"password"`
   Question string `json:"question"`  
   Answer   string `json:"answer"`   
}
```

#### 3.4.2 用户登录

```Go
type LoginByNameRequest struct {
        Username     string  `json:"username"`
        Password     string `json:"password"`
}
```

#### 3.4.3 用户登出

```Go
type LogoutRequest struct {
        SessionID    string `json:"session_id"`
}
```

#### 3.4.4 用户重置密码

```Go
type ResetPasswordRequest struct {
   Username     string `json:"username"`
   Answer  string    `json:"answer"`
   NewPassword     string `json:"new_password"`
}
```

#### 3.4.5 用户上传头像

```Go
//利用post form-data 
File:key:"file"  头像
Text:key:"session_id" 
```

### 3.5 输出项

#### 3.5.1 用户注册

```Go
type Response struct {
    Code      int `json:"code"`                    //返回码，0为成功，1为失败
    Message   string `json:"message"`              //返回信息
}
```

#### 3.5.2 用户登录

```Go
type Response struct {
    Code      int `json:"code"`                    //返回码，0为成功，1为失败
    Message   string `json:"message"`              //返回信息
    SessionId string `json:"session_id"`
    UserAvatar string    `json:"useravatar"`  //用户图像
}
```

#### 3.5.3 用户登出

```Go
type Response struct {
    Code      int `json:"code"`                    //返回码，0为成功，1为失败
    Message   string `json:"message"`              //返回信息
}
```

#### 3.5.4 用户重置密码

```Go
type Response struct {
    Code      int `json:"code"`                    //返回码，0为成功，1为失败
    Message   string `json:"message"`              //返回信息
}
```

#### 3.5.5 用户上传头像

```Go
type Response struct {
    Code      int `json:"code"`                    //返回码，0为成功，1为失败
    Message   string `json:"message"`              //返回信息
    UserAvatar string    `json:"useravatar"`
}
```

### 3.6 算法

MD5消息摘要算法，属Hash算法一类。MD5算法对输入任意长度的消息进行运行，产生一个128位的消息摘要(32位的数字字母混合码)。

### 3.7 流程逻辑 

![img](https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=N2NiYmZkNzc2MTIxMTFjNGRjMjM4OTYyY2Q2NmFkZGRfVjUzRlVtREd3SEhaU1JyR0Qwa0sxU25rekZhRFBpQzNfVG9rZW46Ym94Y25UY0RnUkNyS3M5MDhOVW5HNzhjT2diXzE2NTMwMzY2ODI6MTY1MzA0MDI4Ml9WNA)

![img](https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=NWM5ZGYyYzc2OTMzZGY2OGVjNGYwOTFlNjI5Y2IyM2NfVWR1Ymxna3U4QjdCR0xZcTMycnFzUnF4aHFGTnNxQ0VfVG9rZW46Ym94Y25CSG15NHNJeUEySkJsZVg0Qmc5WFNpXzE2NTMwMzY2ODI6MTY1MzA0MDI4Ml9WNA)

![img](https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=ZDY2MDgwM2VlNjY4NDI0YzUyNWY0ZDNmY2ZhNzJkY2FfSnBHVXVzVlhFdk1BRFkyaGZFSGFYdkgwRTg2eG5vOU5fVG9rZW46Ym94Y25rZUg4bXpkZkNLNkU3TTJmVVBkdFZkXzE2NTMwMzY2ODI6MTY1MzA0MDI4Ml9WNA)

### 3.8 接口 

#### 3.8.1 用户注册

```Go
url := "api/register"
method := "POST"
```

#### 3.8.2 用户登录

```Go
url := "api/login"
method := "POST"
```

#### 3.8.3 用户登出

```Go
url := "api/logout"
method := "POST"
```

#### 3.3.4 用户重置密码

```Go
url := "api/resetpassword"
method := "POST"
```

#### 3.8.4 用户上传头像

```Go
url := "api/uploadavatar"
method := "POST"
```

### 3.9存储分配

| **软件**   | **存储分配**                | **备注**                                           |
| ---------- | --------------------------- | -------------------------------------------------- |
| **服务器** | 内存：50-100MB， 硬盘：50GB | 适当情况下可以扩容，采用分布式集群的方式运行服务端 |
| **数据库** | 内存：1GB； 硬盘：50GB      | 适当情况下可扩容                                   |

### 3.10 注释设计

1.单行注释（single-line）：//注释内容

  一次只能注释一行，一般是简单注释，用来简短描述某个变量或属性，程序块。

2.块注释（block）：/*注释内容*/

 为了进行多行简单注释，一般不使用

### 3.11 限制条件

必须在连接互联网的情况下才能使用本模块，否则将提示网络异常信息。

### 3.12 测试计划

在网站上验证上述功能

### 3.13 尚未解决的问题

接口字段的模糊混淆处理，所以还是存在非法用户进行恶意发送脏请求的可能。

## 4 分享模块 设计说明  

### 4.1 程序描述

在用户登录的情况下，用户可以在主页点击“分享表情包”进入表情包分享服务。对于发布新的表情包，用户可以选择上传图片，图片从用户本地，上传到网站服务器上；选择表情包的类别。

### 4.2 功能

| 功能                   | 格式/请求 | 功能描述                  |
| ---------------------- | --------- | ------------------------- |
| 发表                   | json/POST | 用户发表表情包            |
| 通过content获得shareID | json/POST | 获取shareID               |
| 修改share              | json/POST | 修改分享的表情包          |
| 删除share              | json/POST | 删除用户直接上传的表情包  |
| 请求share              | json/POST | 一次性请求多条share的信息 |

### 4.3 性能

| 运行                   | 模块组合                               | 响应时间(ms) |
| ---------------------- | -------------------------------------- | ------------ |
| 发表                   | 分享管理模块、数据库模块、用户管理模块 | 100ms        |
| 通过content获得shareID | 分享管理模块、数据库模块               | 100ms        |
| 修改share              | 分享管理模块、数据库模块               | 100ms        |
| 删除share              | 分享管理模块、数据库模块、用户管理模块 | 100ms        |
| 请求share              | 分享管理模块、数据库模块               | 10ms         |

### 4.4 输入项

#### 4.4.1 发表share

用户上传表情包，将表情包图片放置到sticker文件夹下，修改sticker表，另外将路径，文字保存到share表中。

```Go
url := "api/newshare"
method := "POST"
```

#### 4.4.2 通过content获得shareID

```Go
type GetShareIdRequest struct{
    Content string `json:"content"`
    SessionId string `json:"session_id"`
}
```

#### 4.4.3 修改share

```Go
//利用post form-data的格式传输文字，图片
Text:key:"session_id" 
Text:key:"share_id"
Text:key:"content" 新的内容
```

#### 4.4.4 删除share

```Go
type DeleteShareRequest struct {
    SessionId string `json:"session_id"`
    ShareId   uint   `json:"share_id"`
}
```

#### 4.4.5 请求share

```Go
type GetShareRequest struct {
    SessionId string `json:"session_id"`
    PageNum int `json:"page_num"` // 当前请求的页号 1开始计数
}
```

### 4.5 输出项 

#### 4.5.1 发表share

```Go
type Response struct {
    Code      int `json:"code"`                    //返回码，0为成功，1为失败
    Message   string `json:"message"`              //返回信息
}
```

#### 4.5.2 通过content获得shareID

```Go
type Response struct {
    Code      int `json:"code"`                    //返回码，0为成功，1为失败
    Message   string `json:"message"`              //返回信息
    Share_id  uint `json:"share_id"`
}
```

#### 4.5.3 修改share

```Go
type Response struct {
    Code      int `json:"code"`                    //返回码，0为成功，1为失败
    Message   string `json:"message"`              //返回信息
}
```

#### 4.5.4 删除share

```Go
type Response struct {
    Code      int `json:"code"`                    //返回码，0为成功，1为失败
    Message   string `json:"message"`              //返回信息
}
```

#### 4.5.5 请求share

```Go
type ShareResponse struct {
   Code   int `json:"code"`
   Shares [] ShareResponseStruct`json:"shares"`
}
```

### 4.6 算法 

无

### 4.7 流程逻辑



<img src="https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=ZjBiMmU1Y2EyNjlhNWI2NWVkNjhjOGZlNzM3ZTU0ODBfSzdWRlJqNG90c1ptTW4yM1ZPZVFSRXY1UnY5TFoxR0NfVG9rZW46Ym94Y25SeVFDZ1B2ckk1RVZjY2xGQnhaWE5lXzE2NTMwMzY2ODI6MTY1MzA0MDI4Ml9WNA" alt="img" style="zoom: 33%;" />



### 4.8 接口

#### 4.8.1 发表share

上传表情包，将表情包图片放置到sticker文件夹下，修改sticker表，另外将路径，文字保存到share表中

```Go
url := "api/newshare"
method := "POST"
```

#### 4.8.2 通过content获得shareId

```Go
url := "api/getshareid"
method := "POST”
```

#### 4.8.3 修改share

```Go
url := "api/editshare"
method := "POST"
```

#### 4.8.4 删除share

```Go
url := "api/deleteshare"
method := "POST"
```

#### 4.8.5 请求share

```Go
url := "api/getshare"
method := "POST“
```

### 4.9存储分配

| **软件**   | **存储分配**                | **备注**                                           |
| ---------- | --------------------------- | -------------------------------------------------- |
| **服务器** | 内存：50-100MB， 硬盘：50GB | 适当情况下可以扩容，采用分布式集群的方式运行服务端 |
| **数据库** | 内存：1GB； 硬盘：50GB      | 适当情况下可扩容                                   |

### 4.10 注释设计

1. 单行注释（single-line）：//注释内容

  一次只能注释一行，一般是简单注释，用来简短描述某个变量或属性，程序块。

2. 注释（block）：/*注释内容*/

 为了进行多行简单注释，一般不使用。

### 4.11 限制条件

必须在连接互联网的情况下才能使用本模块，否则将提示网络异常信息。

###  4.12 测试计划

在网站上验证上述功能

### 4.13 尚未解决的问题

无

## 5 评论模块 设计说明  

### 5.1 程序描述

用户在登录的情况下，可以对分享的表情包进行评论。

### 5.2 功能

| 功能         | 格式/请求 | 功能描述                                                     |
| ------------ | --------- | ------------------------------------------------------------ |
| 新建评论     | json/POST | 用户可以对分享进行评论。页面将会显示评论用户，评论内容，评论点赞数以及评论时间。 |
| 删除评论     | json/POST | 返回对应share的所有评论100ms                                 |
| 点赞评论     | json/POST | 用户可以删除自己的评论。                                     |
| 修改评论点赞 | json/POST | 用户可以对评论点赞，同一条评论只能点赞一次。                 |

### 5.3 性能

| 运行         | 模块组合           | 响应时间(ms) |
| ------------ | ------------------ | ------------ |
| 新建评论     | 网络模块、评论模块 | 100ms        |
| 删除评论     | 网络模块、评论模块 | 100ms        |
| 点赞评论     | 网络模块、评论模块 | 50ms         |
| 修改评论点赞 | 网络模块、评论模块 | 50ms         |

### 5.4 输入项

#### 5.4.1 新建评论

```Go
type NewCommentRequest struct {
    ShareId      uint         `json:"share_id"`
    SessionId    string      `json:"session_id"`
    Content      string      `json:"content"`
}
```

#### 5.4.2 请求评论

```Go
type GetCommentRequest struct {
    ShareId     int         `json:"share_id"`
}
```

#### 5.4.3 删除评论

```Go
type DeleteCommentRequest struct {
    CommentId     uint       `json:"comment_id"`
    SessionId    string      `json:"session_id"`
}
```

#### 5.4.3 修改评论点赞

```Go
type CommentLikeRequest struct {
    CommentId     uint        `json:"comment_id"`
    SessionId    string      `json:"session_id"`
}
```

### 5.5 输出项

#### 5.5.1 新建评论

```Go
type Response struct {
    Code      int `json:"code"`                    //返回码，0为成功，1为失败
    Message   string `json:"message"`              //返回信息
}
```

#### 5.5.2 请求评论

```Go
type CategoryResponse struct {
   Code   int     `json:"code"`
   CommentItems [] CommentItem `json:"comment_items"`
}
```

#### 5.5.3 删除评论

```Go
type Response struct {
    Code      int `json:"code"`                    //返回码，0为成功，1为失败
    Message   string `json:"message"`              //返回信息
}
```

### 5.6 算法

无

### 5.7 流程逻辑



![img](https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=Y2MwNWI0MzMxZjM3MWQ3N2E1NTc3ZDU0ODg1MmUwNjJfZUx1VmR6YnJjZEJzZHdyT0dPd21haUEwZ0ZMRVYyZG5fVG9rZW46Ym94Y24wRm91QkFSd2tGRHFzMnR1MDNrdWJWXzE2NTMwMzY2ODI6MTY1MzA0MDI4Ml9WNA)



### 5.8 接口

#### 5.8.1 新建评论

```Go
url:="api/newcomment"
method := "POST"
```

#### 5.8.2 请求评论

```Go
url:="api/getcomment"
method := "POST"
```

#### 5.8.3 删除评论

```Go
url:="api/deletecomment"
method := "POST"
```

#### 5.8.4 修改评论点赞

```Go
url:="api/altercommentlike"
method := "POST"
```

### 5.9存储分配

| **软件**   | **存储分配**                | **备注**                                           |
| ---------- | --------------------------- | -------------------------------------------------- |
| **服务器** | 内存：50-100MB， 硬盘：50GB | 适当情况下可以扩容，采用分布式集群的方式运行服务端 |
| **数据库** | 内存：1GB； 硬盘：50GB      | 适当情况下可扩容                                   |

### 5.10 注释设计

1. 单行注释（single-line）：//注释内容

  一次只能注释一行，一般是简单注释，用来简短描述某个变量或属性，程序块。

2. 块注释（block）：/*注释内容*/

  为了进行多行简单注释，一般不使用。

### 5.11 限制条件

必须在连接互联网的情况下才能使用本模块，否则将提示网络异常信息。

### 5.12 测试计划

在网站上验证上述功能

### 5.13 尚未解决的问题  

无

## 6 收藏模块 设计说明 

### 6.1 程序描述

在用户登录的情况下，用户可以收藏或取消网站中所有的表情包。

### 6.2 功能

| 功能     | 格式/请求 | 功能描述             |
| -------- | --------- | -------------------- |
| 新建收藏 | json/POST | 用户收藏某个表情包   |
| 删除收藏 | json/POST | 用户删除收藏的表情包 |

### 6.3 性能

| 运行     | 模块组合             | 响应时间(ms) |
| -------- | -------------------- | ------------ |
| 新建收藏 | 收藏模块、数据库模块 | 100ms        |
| 删除收藏 | 收藏模块、数据库模块 | 100ms        |

### 6.4 输入项

#### 新建收藏

```Go
type NewCollectionRequest struct {
    StickerId uint   `json:"sticker_id"`
    SessionId string `json:"session_id"`
}
```

#### 删除收藏

```Go
type DeleteCollectionRequest struct {
    SessionId    string `json:"session_id"`
    CollectionId uint   `json:"collection_id"`
}
```

### 6.5 输出项

#### 6.5.1 新建收藏

```Go
type Response struct {
    Code      int `json:"code"`                    //返回码，0为成功，1为失败
    Message   string `json:"message"`              //返回信息
}
```

#### 6.5.2 删除收藏

无

### 6.6 算法

无

### 6.7 流程逻辑

![img](https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=ZThjYzhlZDBlZjMxNGYzOWZhMzEyM2QxMzZmMmY0Y2FfWkhna25rNm1QVWVzU0RUN0lSUjVWYlFzdGdvT0hqajBfVG9rZW46Ym94Y25ZRWp3ckpOS1RpcFRvNDhYVkRlS2ZLXzE2NTMwMzY2ODI6MTY1MzA0MDI4Ml9WNA)

### 6.8 接口 

用图的形式说明本程序所隶属的上一层模块及隶属于本程序的下一模块、参数赋值和调用方式，说明与本程序具有直接关系之数据结构（数据库、数据文卷）

### 6.9存储分配

| **软件**   | **存储分配**                | **备注**                                           |
| ---------- | --------------------------- | -------------------------------------------------- |
| **服务器** | 内存：50-100MB， 硬盘：50GB | 适当情况下可以扩容，采用分布式集群的方式运行服务端 |
| **数据库** | 内存：1GB； 硬盘：50GB      | 适当情况下可扩容                                   |

### 6.10 注释设计

1.单行注释（single-line）：//注释内容

  一次只能注释一行，一般是简单注释，用来简短描述某个变量或属性，程序块。

2.块注释（block）：/*注释内容*/

 为了进行多行简单注释，一般不使用

### 6.11 限制条件

必须在连接互联网的情况下才能使用本模块，否则将提示网络异常信息。

### 6.12 测试计划

在网站上验证上述功能

### 6.13 尚未解决的问题

接口字段的模糊混淆处理，所以还是存在非法用户进行恶意发送脏请求的可能。