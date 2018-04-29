# 实验四：图书管理系统顺序图绘制

|学号|班级|姓名|
|:----:|:----:|:----:|
|201510414118|15级软工一班|任翔|

## 1.管理员
### 1.1 源码
```
@startuml

hide footbox

actor 读者 as reader
participant 注册系统 as registersystem
actor 普通管理员 as manager
actor 超级管理员 as superManager
participant 管理系统 as managersystem
database mysql

activate reader
activate registersystem
activate manager
activate managersystem
activate mysql
reader -> registersystem : 发送请求（申请会员、申请普通管理员）
registersystem --> registersystem : 是否已经缴费
registersystem -> manager : 缴费成功，申请会员
manager -> managersystem : addmember()
managersystem --> managersystem : checklevel()
managersystem -> mysql :2.可以对数据部分修改（会员请求）
mysql --> managersystem
managersystem -> manager : 申请会员确认
manager -> registersystem : 申请会员成功
deactivate manager
activate superManager
registersystem -> superManager :申请普通管理员
managersystem -> mysql : 可以对数据更改
mysql --> managersystem
managersystem -> superManager : 确认管理员申请
superManager -> registersystem: 申请普通管理员成功
registersystem -> reader : 回复请求

@enduml
```
### 1.2图片

![](./test4_manager.png '描述')

## 2.借书
### 2.1源码
```
@startuml

actor 读者 as reader
actor 管理员 as manager
participant 借书系统 as system
participant item
database mysql

activate reader
activate manager
activate system
activate item
activate mysql

reader -> manager : 借阅书籍
manager -> system : login()
system --> system : loginCheck()
system -> item : select()
item -> mysql : 数据库查询
mysql --> item 
item -> system : feedback()
note right : 返回读者的基本信息\n借阅书籍信息
note left : 借书超时需缴纳费用
system -> manager : 1. 拒绝借书
system -> manager : 2. 可以借书
manager -> system : select()
system -> item : bookinfor()
item -> mysql : 数据库查询
mysql --> item
item -> system : feedback()
note right : 可以的借阅书籍
manager -> system : add()
system -> item : addBook()
item -> mysql : 查询并更改数据库
mysql --> item
item -> system : feedback()
system -> manager : 确认
manager -> reader : 借书成功
@enduml
```
### 2.2图片

![](./test4_lendBook.png '描述')

## 3.还书
### 3.1源码
```
@startuml

actor 读者 as reader
actor 管理员 as manager
participant 借书系统 as system
participant item
database mysql

activate reader
activate manager
activate system
activate item
activate mysql

reader -> manager : 归还书籍
manager -> system : login()
system --> system : loginCheck()
system -> item : select()
item -> mysql : 数据库查询
mysql --> item 
item -->item : bookTimeCheck()
note right : 是否有逾期书籍
item -> system : feedback()
note right : 返回读者的基本信息\n借阅书籍信息
note left : 借书超时需缴纳费用
manager -> reader : 收取费用
manager -> system : finecheck()
system -> item : pay()
item -> mysql : 查询并更改数据库
mysql --> item
item -> system : feedback()
manager -> system : return()
note left : 如果没有超时直接到此步骤
system -> item : returnBook()
item -> mysql : 查询并更改数据库\n
mysql --> item
item -> system : feedback()
system -> manager : 确认
manager -> reader : 还书成功
@enduml
```
### 3.2图片

![](./test4_returnBook.png '描述')

## 4.预定图书
### 4.1源码
```
@startuml

actor 读者 as reader
participant 借书系统 as system
participant item
database mysql

activate reader
activate system
activate item
activate mysql

reader -> system : login()
system --> system : loginCheck()
system -> item :  select()
item -> mysql : 查询数据库
mysql --> item
item -> system : feedback()
note right : 返回读者基本信息\n可借书籍信息
reader -> system : book()
system -> item : bookBook()
item -> mysql : 更新数据库
mysql --> item
item -> system : feedback()
system -> reader : 预订成功
@enduml
```
### 4.2图片
![](./test4_bookBook.png '描述')

## 5.取消预订图书
### 5.1源码
```
@startuml

actor 读者 as reader
participant 取消预定书籍系统 as system
participant item
database mysql

activate reader
activate system
activate item
activate mysql

reader -> system : login()
system --> system : loginCheck()
system -> item :  select()
item -> mysql : 查询数据库
mysql --> item
item -> system : feedback()
note right : 返回读者基本信息\n借书信息\n可借书籍
reader -> system : cancelbook()
system -> item : cancelbookBook()
item -> mysql : 更新数据库\n删除预定书籍
mysql --> item
item -> system : feedback()
system -> reader : 预订成功
@enduml

```
### 5.2图片

![](./test4_cancelbook.png '描述')