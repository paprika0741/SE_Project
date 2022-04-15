## 需求分析报告

## 1 引言

### 1.1 编写目的

在移动互联网时代，图像文本以网络表情包的方式呈现，依托社会热点实现更新换代。网络表情包通常以简洁、有趣的图片承载复杂的信息和内涵，受众更易识记和理解，它适应了现代社会人们的交流需求得以广泛传播。表情包文化悄然兴起，作为新兴的流行话语体系，网络表情包借助即时通讯软件日渐渗透于大众的日常工作和生活，改变了人们的表达和交流方式，并对社会产生深远影响。

当今聊天软件中，大家对于表情包的使用非常的频繁，表情包作为聊天中必不可少的工具，这是基于网络社交而出现的一种方式，以前我们聊天只是以文字的内容，现在多了表情包，有时候甚至可以用表情包来对话。表情包作为一种新的沟通媒介，能够表达出我们不同的感情，其逐渐成为了网络聊天中不可或缺的一部分，优质的表情包也成为了大家都希望获得的资源，所以我们的项目就是一个可以用来方便的分享、下载并管理表情包的网络平台，方便大家把自己制作的表情包分享给更多的人，也是一个方便的平台来让大家获取更多有趣的表情包。



### 1.2 预期读者

小组成员，老师和助教

### 1.3 参考资料

[软件项目需求分析报告模板_lusanshui的博客-程序员宅基地_需求分析报告模板 - 程序员宅基地](https://cxyzjd.com/article/lusanshui/85243045)

课件： *Lecture09 - Requirements Analysis*

## 2 需求概述

### 2.1 原始需求

产品是一个应用平台，解决表情包的分享和推荐功能。

为用户提供一个上传或者下载表情包的平台，但是平台不提供原创的表情包，只是一个帮助表情包流通的平台。

系统根据网站和用户信息向特定的用户推荐特定的表情包，方便用户获取到自己想要的表情包。

### 2.2 用户

与本产品交互的用户有：

- 用户，接口为网站
- 网站管理员，可以查看网站数据库中的统计信息
- 开发人员，可以查看并编辑本产品的代码
- 数据库维护人员，本产品依赖了数据库系统，所以该数据库的提供者可以修改数据库的接口

### 2.3 目的

首先是因为表情包的需求量很大，表情包逐渐成为聊天不可或缺的，所以会有很多的网友在网上搜集表情包供自己聊天使用。

表情包作为一种有趣的信息表达形式，其不像是一些资源（如：产品信息，具有商业价值的文档）等，拥有表情包的意义是在于与别人交流所用，而拥有表情包的乐趣会在与他人产生共鸣后增加，所以用户在拥有了有趣的表情包时，也需要有一个平台可以与其他人分享。

所以本个平台对于上传和下载表情包的用户都会满足各自的需求。

## 3 功能实例化

### 3.1 用户注册

对于新用户创建个人账户，系统应在登陆界面显示“用户注册”的连接，然后提示用户输入用户名、用于验证的手机号或者邮箱，系统返回用户的输入是否合法，包括用户名是否已存在，手机号或者邮箱格式是否正确、是否已被注册，从系统中储存的图形验证码中随机选择一张加载到网页中，提示用户输入图形验证码，并识别用户输入的图形验证码是否正确

当用户按要求输入后，若用户选择使用手机号验证，则后台通过电信运营商发送短信验证码到用户输入的手机号中，并在网页上提示用户输入验证码；若用户选择使用邮箱验证，后台通过邮箱服务器发送验证链接到用户输入邮箱

若验证失败，则提示用户，并给出错误信息，如“验证码错误”“服务器失去链接”；若验证成功，提示用户输入密码，并提示密码要求：长度大于8个字符，包含数字和字母，不能含有特殊字符；当用户输入一次密码后，验证该密码字符串是否符合密码要求，若符合，提示用户再次输入密码确认；若不符合，提示用户更换密码；提示用户输入密保问题和答案

密码验证通过后，显示注册成功，并进入网站功能导览；服务器把用户的相关信息，存入服务器，密码信息需要用md5加密储存

### 3.2 用户登陆

登陆界面，显示登录选项，可以使用用户名登录、手机号登录、邮箱登录

对于使用用户名登录，显示输入用户名和密码的界面

对于使用手机号登录，显示输入手机号和密码的界面，还有可以选择使用手机验证码的选项（发送验证码的流程与用户注册中一样）

对于使用邮箱登录，显示输入邮箱和密码的界面

另外界面下方提供“忘记密码”的选项，用户输入注册时使用的手机号或邮箱验证后，输入密保问题答案，进入用户修改密码或密保功能

把用户输入的信息通过网络传入到服务器中，并与服务器的数据库信息进行比对，若匹配则成功；若不匹配，若无该用户或手机邮箱，提示“用户不存在”；若密码错误，提示“密码错误，请再次输入”；若因网络问题无法连接到服务器，提示“网络连接异常”；若服务器异常，提示“服务器异常，请稍后”

用户成功登录后，进入主界面

### 3.3 用户修改个人资料

在用户登录的情况下，用户可以点击“修改个人资料”，进入用户修改个人资料功能

用户可修改的资料有：绑定的手机号、绑定的邮箱、个人喜好

修改绑定手机号或者绑定邮箱的流程为：输入账号密码，输入新的手机号或者邮箱，验证（与注册的验证过程相同）

对于个人喜好，用户可以随意编辑，当用户点击保存后，服务器中数据库的信息同步修改

### 3.4 用户修改密码或密保

在用户登录的情况下，用户可以选择修改密码

首先验证绑定的邮箱或者手机号，通过后，可以进入修改用户修改密码或者密保功能

提示用户输入原密码，和新密码，对新密码进行验证，再次输入新密码，服务器数据库修改相应的密码信息

### 3.5 表情包分享服务

在用户登录的情况下，用户可以在主页点击“分享表情包”进入表情包分享服务

对于发布新的表情包，用户可以选择上传图片，图片从用户本地，上传到网站服务器上；选择表情包的类别

表情包发布，服务器存入数据库中，并且显示在其他用户的界面中

用户可以修改或者删除自己发表的表情包，可以点赞其他用户分享的表情包，并会在所有用户的界面中显示该条表情包的赞数

### 3.6 评论服务

在用户的登录状态下，用户可以评论自己或者其他用户发表的表情包，评论的信息存入数据库中，并显示在其他用户的界面中，并且提醒该表情包的发布用户

用户可以点赞或者取消点赞其他用户的评论，系统对其的处理与处理表情包的点赞一致

### 3.7 收藏服务

在用户登录的情况下，用户可以收藏或取消网站中所有的表情包，服务器数据库中会添加被用户收藏的表情包序号，并且根据用户收藏的表情包进行分析

### 3.8 站点系统管理服务

站点系统管理服务将提供管理员查看站点运行状态，维护并管理功能。

### 3.9 后端事务服务

后端事务管理将为站点管理员提供帐户管理，统计用户信息、个性化推荐服务。





## SRS

### 1 引言

#### 1.1简介

本项目是一个表情包图片分享网页项目，整个系统包括登录模块，分享模块，评论模块，推荐模块。

#### 1.2范围

#### **1.2.1 产品应用功能范围**

项目是一个可以用来方便的分享、下载并管理表情包的网络平台，方便大家把自己制作的表情包分享给更多的人，也是一个方便的平台来让大家获取更多有趣的表情包。用户可以分享，收藏，点赞，评论表情包，系统会分享用户喜好进行个性化推荐。

#### **1.2.2 产品收益及目标**

产品旨在提供分享原创表情包平台，帮助用户寻找和分享表情包，不做商业用途。

#### 1.3 定义、简写和缩略语

HTTP: 超文本传输协议（Hyper Text Transfer Protocol，HTTP）是一个简单的请求-响应协议，它通常运行在TCP之上。它指定了客户端可能发送给服务器什么样的消息以及得到什么样的响应。

MYSQL：MySQL 是最流行的关系型数据库管理系统，在 WEB 应用方面 MySQL 是最好的RDBMS(Relational Database Management System：关系数据库管理系统)应用软件之一。

UML：一种编制软蓝图的标准化语言，它的目标之一就是为开发团队提供标准通用的设计语言来开发和构建计算机应用。

用例图：指由参与者、用例以及它们之间的关系构成的用于描述系统功能的静态视图。

类图：常用的UML图，显示出类、接口以及它们之间的静态结构和关系；它用于描述系统的结构化设计。

活动图：用于描述系统行为的模型视图，它可用来描述动作和动作导致对象状态改变的结果，而不用考虑引发状态改变的事件。

状态图：描述一个实体基于事件反应的动态行为，显示了该实体如何根据当前所处的状态对不同的事件做出反应的。

协作图：显示对象之间如何进行交互以执行特定用例或用例中特定部分的行为。

#### 1.4 引用文件

《GBT 9385-2008 计算机软件需求规格说明规范》

#### 1.5 综述

第二部分是项目的总体描述，介绍产品描述，产品功能，用户特定，约束，假设和依赖关系和需求分配。第三部分介绍具体需求。在第三部分中，分模块具体介绍拟实现的功能，性能需求，数据库逻辑设计，软件系统属性。



### 2 总体描述

#### 2.1 产品描述

##### 2.1.1 用户界面

注册页面：显示用户名，用户密码，密保问题，验证手机号，邮箱账号的输入框。对于输入的合法性返回提示信息。

登录页面：显示用户名，密码的输入框。输入的合法性返回提示信息。提供跳转到修改密码的链接

修改密码页面：显示密保问题，提示用用户输入密保问题答案，和两次输入新密码。对于输入的合法性返回提示信息。

用户资料页面：显示用户的资料信息：用户名，用户头像，喜好，

表情包主页：显示表情包及其描述。根据用户的喜好以及当前热点推荐。表情包下方显示点赞，收藏，评论数目。

表情包分类页面：输入框供用户输入表情包类别，显示分类结果。表情包下方显示点赞，收藏，评论数目。

新建分享页面：显示上传图片，输入描述，分类信息的输入框。

收藏页面：显示用户的收藏图片

评论页面：显示用户分享的评论内容以及评论点赞信息

新建评论页面：显示评论输入框以及输入完成的确认建。对于输入的合法性返回提示信息。

**活动图**：

<img src="https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=MzkwOWViYWFjODU3NjJhOTQxMGY5ZTBlOTdmMTZiOTVfWEJ4alJ4Y1Z1M1pyb1BEbzZNRTBFaDI5TGZBSGhmRjVfVG9rZW46Ym94Y241eXRmZTd1alpVMWVBd3NsWklrSWVoXzE2NTAwMTE0MDQ6MTY1MDAxNTAwNF9WNA" alt="img" style="zoom:80%;" />

##### 2.1.2 硬件接口

键盘：用户输入文字描述等

鼠标：用户点击页面跳转

屏幕：显示页面

##### 2.1.3 软件接口

使用的数据库操作系统为MySQL，版本 Server version: 8.0.27 MySQL Community Server - GPL。来源：MySQL AB 公司开发，属于 Oracle 旗下产品。

连接MySQ接口使用go的Gin框架，版本号为 1.4.0。Gin框架是使用 Go/golang 语言实现的 HTTP Web 框架.

##### 2.1.4通信接口

HTTP、HTTPS应用层传输协议：前端通过请求接口路径来和后端通信。请求方法包括POST/GET/PUT/DELETE。

##### 2.1.5内存约束

内存支持最低512MB

磁盘支持最低2G

#### 2.2 产品功能

用户服务可以提供用户注册(检测用户名是否重复)，用户登录，用户登出，设置用户资料，密保问题，修改密码等服务。

表情包分享服务将提供表情包分类检索用户分享，删除分享，修改分享，点赞分享等功能。

评论服务将提供评论分享，点赞评论，取消点赞评论等功能。

收藏服务将提供收藏分享，取消收藏等功能。

站点系统管理服务将提供管理员查看站点运行状态，维护并管理功能。

后端事务管理将为站点管理员提供帐户管理，统计用户信息、个性化推荐服务。

**客户用例图：**

 

<img src="https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=ZDg4OTliZjlkMWRjYjNkN2QzMDRiZDIyNTkxZDcyYzBfSWpYMUtZMkl2Tk5hQ2d0NWpvRkdkNlU5VG00QlN5WXVfVG9rZW46Ym94Y25QU0xyWWl2VWNBUHR0NTBPQlR5WlJmXzE2NTAwMTE0MDQ6MTY1MDAxNTAwNF9WNA" alt="img" style="zoom: 33%;" />

**管理员用例图：**

<img src="https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=N2YyYTk4M2FlMzUxYTkzNWMyYTA4NmYwZWMyYjQ4ZWFfUVhmMWtYWWR5UWZtZlZiY1dreUJacHZIT3YzQTB2SVFfVG9rZW46Ym94Y25GVFY3Y3NtYWRWMFl4eDNQbDBNZk9nXzE2NTAwMTE0MDQ6MTY1MDAxNTAwNF9WNA" alt="img" style="zoom:33%;" />

**类图：**

<img src="https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=NDM3YTEyZWY4NmVhMTNkZDQyZjI2YjA0YThjYzVkYTVfbTFOOTVLelNpQVZpNzdXd1dBQ0pLRGpVb2huTXJUeXVfVG9rZW46Ym94Y25sdVZVdDI4dXQwbzU5U2tDRmlBODRuXzE2NTAwMTE0MDQ6MTY1MDAxNTAwNF9WNA" alt="img" style="zoom: 80%;" />

**状态图**：

<img src="https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=Nzk1ZmZiYWJjY2NjNjU1ODgyY2EwMGU2MzQ3YjI4MjBfdk5tYmZTNDczZXdhY0U2bzZIZkFyOUVvTW1iSVByZGtfVG9rZW46Ym94Y25ma0RGUUZjZDJrU25BMktKekhYQmxnXzE2NTAwMTE0MDQ6MTY1MDAxNTAwNF9WNA" alt="img" style="zoom:67%;" />

#### 2.3 用户特点

最终用户特点：最终用户主要是表情包使用者以及表情包分享者

操作人员的教育水平和技术专长：本科/软件开发

维护人员的教育水平和技术专长：本科/软件开发

#### 2.4 约束

(1) 用于开发的平台（VUE）因为版权或者政治问题不能使用

(2) 国家对于社交媒体平台的管控严格，我们达不到国家的要求，导致不能上线

(3) 租用的服务器计算能力有限、数据库储存的数据信息有限，不能满足需求

(4) 因为采用前后端分离的设计方式，前端和后端之间的接口会有不兼容的问题

(5) 服务器对于超大数量级的请求并行处理能力

(6) 服务器的安全性，对于用户个人信息，包括密码和网站记录的保护

(7) 平台服务器的可靠性

#### 2.5 假设和依赖关系

(1) 开发经费限制：预期在500元以内；

(2) 开发人员限制：小组三人；

(3) 开发期限：整个项目的最晚完成期限是2022年6月30日；

### 3 具体需求

#### 3.1外部接口

(1) 用户上传图片的端口

(2) 用于用户把自己本地的或者其云端网盘上的图片传入网站，每张图片不超过100M

(3) 用户对于表情包的评论

(4) 用户输入对于表情包的评论，100个字以内，unicode编码

#### 3.2功能

##### 3.2.1 用户注册

对于新用户创建个人账户，系统应在登陆界面显示“用户注册”的连接，然后提示用户输入用户名、用于验证的手机号或者邮箱，系统返回用户的输入是否合法，包括用户名是否已存在，手机号或者邮箱格式是否正确、是否已被注册，从系统中储存的图形验证码中随机选择一张加载到网页中，提示用户输入图形验证码，并识别用户输入的图形验证码是否正确

当用户按要求输入后，若用户选择使用手机号验证，则后台通过电信运营商发送短信验证码到用户输入的手机号中，并在网页上提示用户输入验证码；若用户选择使用邮箱验证，后台通过邮箱服务器发送验证链接到用户输入邮箱

若验证失败，则提示用户，并给出错误信息，如“验证码错误”“服务器失去链接”；若验证成功，提示用户输入密码，并提示密码要求：长度大于8个字符，包含数字和字母，不能含有特殊字符；当用户输入一次密码后，验证该密码字符串是否符合密码要求，若符合，提示用户再次输入密码确认；若不符合，提示用户更换密码；提示用户输入密保问题和答案

密码验证通过后，显示注册成功，并进入网站功能导览；服务器把用户的相关信息，存入服务器，密码信息需要用md5加密储存

**时序图**:

<img src="https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=Y2IxODYxOTA1Y2EwNjRiNGM3NzhmNjU3MjljNjAwZTFfWm02SG5UR2NVUHVJWGgwN24yTGtSdFZRZGlXaVR3aDdfVG9rZW46Ym94Y241UHVybDVnU1MwR1RrZnpEbFRrWmZmXzE2NTAwMTE0MDQ6MTY1MDAxNTAwNF9WNA" alt="img" style="zoom: 67%;" />

**协作图**：

<img src="https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=YjNiNTYxNzAzOTI2NGFlNTYwMGQ0MjE2NTg4OTk0NzNfbEpOamFjOUpqaU1vU3g0NVE3RWpQaDV6TzFSeG9KQjNfVG9rZW46Ym94Y25iTUFhY1phQllVSDdwWEUwejVDUjBnXzE2NTAwMTE0MDQ6MTY1MDAxNTAwNF9WNA" alt="img" style="zoom:67%;" />

##### 3.2.2 用户登陆

登陆界面，显示登录选项，可以使用用户名登录、手机号登录、邮箱登录

对于使用用户名登录，显示输入用户名和密码的界面

对于使用手机号登录，显示输入手机号和密码的界面，还有可以选择使用手机验证码的选项（发送验证码的流程与用户注册中一样）

对于使用邮箱登录，显示输入邮箱和密码的界面

另外界面下方提供“忘记密码”的选项，用户输入注册时使用的手机号或邮箱验证后，输入密保问题答案，进入**用户修改密码或密保**功能

把用户输入的信息通过网络传入到服务器中，并与服务器的数据库信息进行比对，若匹配则成功；若不匹配，若无该用户或手机邮箱，提示“用户不存在”；若密码错误，提示“密码错误，请再次输入”；若因网络问题无法连接到服务器，提示“网络连接异常”；若服务器异常，提示“服务器异常，请稍后”

用户成功登录后，进入主界面

**时序图**：

<img src="https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=Njk5NWQ0ZGY4NjlmNzBkOTU3NTY4OGU3MTg5NWE4NzdfaVFiOTdrZ084YXdoVmZkRWtqRWFhM3FTTEQzalRlcmdfVG9rZW46Ym94Y25oYURZWlh5VFc0ekg5SjVOVWdRQ2JCXzE2NTAwMTE0MDQ6MTY1MDAxNTAwNF9WNA" alt="img" style="zoom: 80%;" />

**协作图**：

<img src="https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=Y2U4ZWJlMjY1ZWY4OTJkZDhlMjEzYjgwOGZmNDBjNjJfYXZ0WWdpR0NONXV6elpYUzltYXpGZGMwaG13M01QU2pfVG9rZW46Ym94Y242VU44QW0zSUI4NVhKOU0yUTFwMjdlXzE2NTAwMTE0MDQ6MTY1MDAxNTAwNF9WNA" alt="img" style="zoom: 80%;" />

##### 3.2.3 用户修改个人资料

在用户登录的情况下，用户可以点击“修改个人资料”，进入用户修改个人资料功能

用户可修改的资料有：绑定的手机号、绑定的邮箱、个人喜好

修改绑定手机号或者绑定邮箱的流程为：输入账号密码，输入新的手机号或者邮箱，验证（与注册的验证过程相同）

对于个人喜好，用户可以随意编辑，当用户点击保存后，服务器中数据库的信息同步修改

**时序图**：

<img src="https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=MmU1NWNkNDA4N2Q4ZjBhZjVmMmZmNmJmYjBjOWFjYmJfSmxKUkRtdWFBS1pySXRGcHhwRFBMeWNDS1VSYWxWN1RfVG9rZW46Ym94Y25yQk5kMEpvTm95NzliQ2YxaVF2U0tjXzE2NTAwMTE0MDQ6MTY1MDAxNTAwNF9WNA" alt="img" style="zoom:80%;" />

**协作图**：



<img src="https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=NGViZmUxOGI1M2Y2ZjUxM2Q2NTJlMTdiYzE1MmM1ZmRfUldWYUJQemNVUHU0bDA4Vm11NGRDd21TMmlKdHphUEFfVG9rZW46Ym94Y25rZUg4bXpkZkNLNkU3TTJmVVBkdFZkXzE2NTAwMTE0MDQ6MTY1MDAxNTAwNF9WNA" alt="img" style="zoom:80%;" />

##### 3.2.4 用户修改密码或密保

在用户登录的情况下，用户可以选择修改密码

首先验证绑定的邮箱或者手机号，通过后，可以进入修改用户修改密码或者密保功能

提示用户输入原密码，和新密码，对新密码进行验证，再次输入新密码，服务器数据库修改相应的密码信息

##### 3.2.5 表情包分享服务

在用户登录的情况下，用户可以在主页点击“分享表情包”进入表情包分享服务

对于发布新的表情包，用户可以选择上传图片，图片从用户本地，上传到网站服务器上；选择表情包的类别

表情包发布，服务器存入数据库中，并且显示在其他用户的界面中

用户可以修改或者删除自己发表的表情包，可以点赞其他用户分享的表情包，并会在所有用户的界面中显示该条表情包的赞数

**时序图**：

<img src="https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=OGRmNjY5Zjk1OTkyNDFiMTE0ZjU1YmIxYWZjNmIxMjVfam5qdHV0UkNLbGEyUGJicEFreWdoMmZvMXBzZm14YmRfVG9rZW46Ym94Y25kQ0YzaFd3dTMzaE9Yc29nMFlnMG9oXzE2NTAwMTE0MDQ6MTY1MDAxNTAwNF9WNA" alt="img" style="zoom:80%;" />

**协作图**：

<img src="https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=Y2ViMzUxYzMxYmQxYTA2NjJmYWZjNGFhMWY4ZTViZTNfRVJ3OGllb1Z5UEUza0xhM0hud2s2ODlHV0lFcnFodTVfVG9rZW46Ym94Y25sSmIzU0tXbWpCWGlCc1hLbzA3ZWliXzE2NTAwMTE0MDQ6MTY1MDAxNTAwNF9WNA" alt="img" style="zoom:80%;" />

##### 3.2.6 评论服务

在用户的登录状态下，用户可以评论自己或者其他用户发表的表情包，评论的信息存入数据库中，并显示在其他用户的界面中，并且提醒该表情包的发布用户

用户可以点赞或者取消点赞其他用户的评论，系统对其的处理与处理表情包的点赞一致

**时序图**：

<img src="https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=MzdkZTQyNjliMjdkNDUyZjgwYzVlNTBiNTQ1YjEwYTFfQlRjN3VINGNzTlVIRlFFaFhZejVMRExaUElxVU5YeE1fVG9rZW46Ym94Y25jbmxpdEdQNjBMRlNzUVB4SHpXNHpoXzE2NTAwMTE0MDQ6MTY1MDAxNTAwNF9WNA" alt="img" style="zoom:80%;" />

**协作图**：

<img src="https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=NDBkZDQ2M2FlZGU3Y2I2ZmEyMTFhYjJlYWYyM2YyZjNfRExvRmZtSWRFU1hnb2t6WG9WbHRjSThCbHNlV1RuUmxfVG9rZW46Ym94Y25qWVZBcTd1OUxyNWJ4NHpsbGlYZE5kXzE2NTAwMTE0MDQ6MTY1MDAxNTAwNF9WNA" alt="img" style="zoom:80%;" />

##### 3.2.7 收藏服务

在用户登录的情况下，用户可以收藏或取消网站中所有的表情包，服务器数据库中会添加被用户收藏的表情包序号，并且根据用户收藏的表情包进行分析

**时序图**：

<img src="https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=ZTM2ZjM3ZTE2MGU0MTY3YjFkZDExMGE3ZTNmYmUzMTRfc3RweDE5a2JmQU1TRXdIam9abXhCcEhXS0NrMnYwMjhfVG9rZW46Ym94Y256TkpObHRobjJ0Zk5wSmo2U0l1MWdjXzE2NTAwMTE0MDQ6MTY1MDAxNTAwNF9WNA" alt="img" style="zoom:80%;" />

**协作图**：



<img src="https://gawy8intpj.feishu.cn/space/api/box/stream/download/asynccode/?code=OWYwZTBhNmNiNjhhOGFhYjk3MWZlMmNlNDM1NWJiYTBfV1Naa0NaR2JaTWxTS0l4WG5tYkJBdWhLN21KUVI3aVhfVG9rZW46Ym94Y25ZRWp3ckpOS1RpcFRvNDhYVkRlS2ZLXzE2NTAwMTE0MDQ6MTY1MDAxNTAwNF9WNA" alt="img" style="zoom:80%;" />

##### 3.2.8 站点系统管理服务

站点系统管理服务将提供管理员查看站点运行状态，维护并管理功能。

##### 3.2.9 后端事务服务

后端事务管理将为站点管理员提供帐户管理，统计用户信息、个性化推荐服务。

#### 3.3性能需求

静态数量化需求：

(1) 支持同时运行的用户数量: 10000

(2 )要处理的信息量和类型: 图片数据传输

(3）响应时间：0.5s

(4）更新处理时间：0.5s

(5）数据的转换和传送时间：1s

动态数量化需求:

(1)高峰期工作负载可以同时运行的用户数量为:10000

灵活性:

(1)运行环境的变化：适用于现有的流行浏览器，：IE、Firefox、QQ浏览器、Safari、Opera、Google Chrome等

(2)同其他软件的接口的变化；

(3)计划的变化或改进：根据用户的需求不断的对软件进行升级和更新

#### 3.4数据库逻辑需求

##### 3.4.1 数据实体及之间的关系

a.**用户users：**

**user_id：用户的id [PK]**

username：用户名

user_pic: 用户头像 （存储图片的路径）

password：用户的密码

security_id: 密保问题的id

b.**密保问题库*****securities*****：**

**security_id：密保问题的id[PK]**

question：问题

answer：答案

c.**表情包sticker：**

**sticker_id: 表情包的id[PK]**

picture: 表情包的内容（存储图片的路径）

category_id: 类别

like_num: 点赞次数

collection_num: 收藏次数

d.**收藏collection：**

**collection_id: 收藏条目id[PK]**

user_id：用户id

sticker_id: 表情包

e.**类别category：**

**category_id：类别id[PK]**

category_name: 类别的名字

category_description： 类别的描述

f.**分享内容share：**

**share_id:分享内容的id [PK]**

user_id: 用户id

content: 文本内容

sticker_id: 表情包id

like_num: 点赞次数

watch_num: 查看次数

share_time: 分享时间

g.**评论comments：**

**comment_id: 评论id [PK]**

share_id: 分享id

user_id : 用户的id

content: 文本

like_num: 点赞次数

h.**stickerlike：**

user_id : 用户的id

sticker_id: 表情包id

i.**commentlike：**

user_id : 用户的id

comment_id :  评论的id

<img src="https://pig-1307013046.cos.ap-nanjing.myqcloud.com/PigCo/asynccode" alt="img" style="zoom: 67%;" />

##### 3.4.2 不同功能使用的信息类型

a.用户登录功能使用到 ： users

b.分享内容功能使用到 :    share

c.评论功能使用到         :    comments

##### 3.4.3 访问能力

 能承载1s内 10000次以上的数据操作请求

#### 3.5软件系统属性

(1) 可靠性：

在客户端与服务器端通信时，如果网络故障，系统不能出现故障。

(2) 可用性：

有效度:99%

(3)安全保密性：

用户密码采用MD5等技术加密保存

保留用户数据的历史和操作记录

对于关键变量检查完整性，避免越权访问

(4)可维护性：

通过良好的监控，提供对系统内部状态和运行时行为的可见性

为自动化提供良好支持，将系统与标准化工具相集成

避免依赖单台机器（在整个系统继续不间断运行的情况下允许机器停机维护）
