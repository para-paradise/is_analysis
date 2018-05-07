# 实验五:图书管理系统数据库设计与界面设计

|学号|班级|姓名|
|:----:|:----:|:----:|
|201510414118|15级软工一班|任翔|

## 1.数据库二维表

### 1.1读者表

|字段|类型|主键/外键|可以为空|约束|说明|
|:----:|:----:|:----:|:----:|:----:|:----:|
|readerId|char(10)|primary key|no||读者用户的ID|
|readerName|varchar(10)||no||读者姓名|
|lendTime|datetime||no||借书时间|
|returnTime|datetime||no||还书时间'2020/02/02'|
### 1.1.1注册用户表

|字段|类型|主键/外键|可以为空|约束|说明|
|:----:|:----:|:----:|:----:|:----:|:----:|
|Id|char(10)|primary key|no||注册用户ID|
|readerId|char(10)|foreign key|no||外键|
|Name|varchar(10)||no||姓名|
|sex|varchar(10)||no||性别|
|role|varchar(10)|foreign key|no||角色权限相关|
|number|integer||no||可借书数量|

### 1.1.2会员用户

|字段|类型|主键/外键|可以为空|约束|说明|
|:----:|:----:|:----:|:----:|:----:|:----:|
|Id|char(10)|primary key|no||ID|
|readerId|char(10)|foreign key|no||外键|
|Name|varchar(10)||no||姓名|
|sex|varchar(10)||no||性别|
|role|varchar(10)|foreign key|no||角色权限相关|
|number|integer||no||可借书数量|

### 1.2图书表

|字段|类型|主键/外键|可以为空|约束|说明|
|:----:|:----:|:----:|:----:|:----:|:----:|
|bookId|char(10)|primary key|no||书号|
|bookName|varchar(10)||no||书名|
|total|String||no||书籍库存|
|author|varchar(10)||no||作者|
|ISBN|char(18)||no||书籍ISBN|
|publictaion|varchar(10)||no||出版社|
|summery|String||no||书籍概要|

### 1.3管理员表

|字段|类型|主键/外键|可以为空|约束|说明|
|:----:|:----:|:----:|:----:|:----:|:----:|
|managerId|integer|primary key|no||管理员id|
|manageName|char(10)||no||姓名|
|manageNumber|varchar(10)||no||编号|
|managePhone|varchar(11)||no||联系电话|
|manageAddress|varchar(20)||no||联系地址|

### 1.4超级管理员表

|字段|类型|主键/外键|可以为空|约束|说明|
|:----:|:----:|:----:|:----:|:----:|:----:|
|managerId|integer|primary key|no||管理员id|
|manageName|char(10)||no||姓名|
|manageNumber|varchar(10)||no||编号|
|managePhone|varchar(11)||no||联系电话|
|manageAddress|varchar(20)||no||联系地址|

###　1.5借阅信息表

|字段|类型|主键/外键|可以为空|约束|说明|
|:----:|:----:|:----:|:----:|:----:|:----:|
|borrowId|int identity(1,1)|primary key|no||借书编号|
|bookId|char(10)||no||书籍id|
|readerId|char(10)||no||读者id|
|borrowTime|detatime||no||借书时间信息|

## 2.界面设计

### 2.1借书信息界面设计

![](./借书信息.png '描述')

* 用例图参见：读者管理设计用例
* 类图参见：借书类，读者类，管理员类
* 顺序图参见：借书顺序图

### 2.2API接口

#### 借书信息
* 功能：借书查询
* 请求地址： http://localhost:8080/api/mangerSystem/lend.html?borrowId=？
* 请求方法：get
* 请求参数：borrowId : integer

|参数名称|可以为空|说明|
|:----:|:----:|:----:|
|borrowId|no|借书的id号，用于搜索查询|
|method|no|固定为get|

* 返回实例：

```
{
    "code": 200,
    "data": {
            "borrowId": 129,
            "bookId": 3242
            "readerId":201510414118
            "borrowTime": 2015-1-2,
     },
    "msg": "响应成功"
}

```
* 返回参数说明

|参数名称|可以为空|说明|
|:----:|:----:|:----:|
|borrowId|no|借书的id号|
|bookId|no|书籍的id号|
|readerId|no|读者的id号|
|borrowTime|no|借书时间|


#### 增加图书
* 功能：增加图书
* 请求地址： http://localhost:8080/api/mangerSystem/addbook.html?bookId=
* 请求方法：post
* 请求参数：bookId : integer

|参数名称|可以为空|说明|
|:----:|:----:|:----:|
|bookId|no|书籍的id号，用于搜索查询|
|method|no|固定为post|

* 返回实例：

```
{
    "code": 200,
    "data": {
            bookid:s12314
            bookName："《时间简史》"
            bookISBN：159-456-763-5612
            author："史蒂芬·霍金"
            publisher："成都大学出版社"
            total:50
            summary:"著名物理学家史提芬霍金所著"
     },
    "returnmsg": "增加成功"
}

```

* 返回参数说明

|参数名称|可以为空|说明|
|:----:|:----:|:----:|
|bookId|no|书籍的id号|
|bookName|no|书籍的名字|
|bookISBN|no|书籍的ISBN|
|author|no|作者名字|
|publisher|no|出版社|
|total|no|书籍库存|
|summery|no|概要内容|
|bookName|no|书籍的名字|
