# 实验三：图书管理系统领域对象建模

|学号|班级|姓名|
|:----:|:----:|:----:|
|201510414118|15级软工一班|任翔|

# 1.图书管理系统类图
### 1.1类图源码：
```
@startuml

class 注册用户{
    +ID:String
    +name:String  
    +sex:String
    +role:String 
    +number:Interger
}
class 会员{
    +name:String 
    +age:Interger
    +maxBorrowNum:Interger
    +maxBorrowDays:date
    +roletime:date
}
class 预定的记录{
    +booktime:date
    +add()
    +select()
}
class 借书记录{
    +lendtime:date
    +returntime:date
    +add()
    +select()
}
class 逾期记录{
    +continueday:date
    +lastday:date
    +returntime:date
    +add()
    +select()
}
class 超级管理员{
    +mangerId:Interger
    +mangerName:String
    +mangerNumber:String
    +mangerAddress:String
    +mangerPhone:String
    +add()
    +select()
    +delete()
    +update()
}
class 管理员信息{
    +mangerId:Interger
    +mangerName:String
    +mangerNumber:String
    +mangerAddress:String
    +mangerPhone:String
    +add()
    +select()
    +delete()
    +update()
}
class 读者信息{
    +readerId:Interger 
    +readerName:String 
    +lendBookTime:String 
    +returnBookTime:String
    +select()
    +borrow()
    +xujie()
    +yujie()
    +returnBook()
    +findBook()
}
class 图书信息{
    +bookId:Interger
    + bookISBN:String
    +bookName:String 
    +total:Interger 
    +stock:Interger 
    +publisher:String 
    +author:String 
    +summary:String
    +add()
    +select()
    +delete()
    +update()
    +setStatus()
}

读者信息  --*  预定的记录  :借阅
读者信息 --> 借书记录:添加
借书记录 --> 管理员信息:增加借阅信息
借书记录 --> 逾期记录
逾期记录 --> 管理员信息:处理
预定的记录 --> 管理员信息 :增加预定记录
管理员信息  --*  图书信息 :mange
管理员信息  --*  读者信息  :mange
超级管理员 "1" -- "多"管理员信息:contains
读者信息    <|--    注册用户
读者信息    <|--    会员

@enduml


```
### 1.2类图

![](./test3_1.png '描述')

### 类图说明

读者信息有包含了三个种类分别有对应的等级
借书记录、预订记录、逾期记录描述是图书信息类的一部分
会员和注册用户和管理员、超级管理员可以对图书信息类、预借信息类、借阅信息类进行操作但是操作的权限不同
比如：普通管理员只能对BookInfo进行select操作，但是超级管理员能对其进行更多的删改添加操作

# 2.图书管理系统对象图

### 2.1源码
```
@startuml
object 超级管理员信息{
    id：007
    name:"Tom"
    number：23
    adress："science and information college"
    phone：1241255262
}
object 普通管理员{
    id：0107
    name:"Cathelin"
    number：23
    adress："science_and_information_college"
    phone：1255552622
}
object 读者{
    id:s111
    role：a1
    booknumber：654655162165
    lendtime：18-05-01
    returntime：18-5-12
}
object 注册用户{
    id:b111
    name："小红"
    time：18-5-2
    role：0
    number：028-5689423
}
object 会员用户{
    name："小李"
    registtime：18-5-2
    role：a1
    nunber：028-5689423
    maxBorrowNum：12
    maxBorrowTime：10 "天"
}
object 借书记录{
    lendtime：18-2-5
}
object 还书记录{
    returntime：18-3-5
}
object 逾期记录{
    maxBorrowTime：10 "天"
    returntime：18-3-8
}
object 图书信息{
    bookid:s12314
    bookName："《时间简史》"
    bookISBN：159-456-763-5612
    author："奥斯特洛夫斯基"
    publisher："成都大学出版社"
    ......
}
超级管理员信息 --* 普通管理员:管理
普通管理员 --* 图书信息
普通管理员 --* 借书记录
普通管理员 --* 还书记录
普通管理员 --* 逾期记录
普通管理员 --* 读者

读者 *-- 注册用户
读者 *-- 会员用户
@enduml
```
### 2.2图片
![](./test3_2.png '描述')

# 3.类图信息

### 3.1图书管理员类图

源码
```
@startuml
class MangeInfo{
    +mangerId:Interger
    +mangerName:String
    +mangerNumber:String
    +mangerAddress:String
    +mangerPhone:String
    ..getter..
    +getMangerId()
    +getMangerName()
    +getMangerNumber()
    +getMangerAddress()
    +getMangerPhone()
    ..setter..
    +setMangerId()
    +setMangerName()
    +setMangerNumber()
    +setMangerAddress()
    +setMangerPhone()
}
@enduml
```
### 3.1.1图片
![](./test3_3.png '描述')

### 3.2图书信息类图

源码
```
@startuml
class Book{
    +bookId:Interger
    +bookISBN:String
    +bookName:String 
    +total:Interger 
    +stock:Interger 
    +publisher:String 
    +author:String 
    +summary:String
    ..getter..
    +getBookId()
    +getBookISBN()
    +getBookName()
    +getTotal()
    +getStock()
    +getPublisher()
    +getAuthor()
    +getSummary()
    ..setter..
    +setBookId()
    +setBookISBN()
    +setBookName()
    +setTotal()
    +setStock()
    +setPublisher()
    +setAuthor()
    +setSummary() 
}

@enduml
```
### 3.2.1图片
![](./test3_4.png '描述')

### 3.3读者信息类图

源码

```
@startuml
class ReaderInfo{
    +readerId:Interger 
    +readerName:String 
    +lendbookid:Interger
    +lendBookTime:String 
    +returnBookTime:String
    ..getter..
    +getReaderId()
    +getReaderName()
    +getLendBookid()
    +getLendBookTime()
    +getReturnBookTime()
    ..setter..
    +setReaderId()
    +setReaderName()
    +setLendBookid()
    +setLendBookTime()
    +setReturnBookTime() 
}
@enduml

### 3.3.1图片

![](./test3_5.png '描述')