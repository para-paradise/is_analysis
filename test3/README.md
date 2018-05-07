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
    +select()
    +update()
    +delete()
    +pay()
}
class 会员{
    +id:String 
    +readerId:String
    +Name:String
    +sex:String
    +role:String
    +number:integer
    +select()
    +update()
    +delete()
    +pay()
}
class 借阅信息{
    +borrowid:Interger
    +bookid:char
    +readerid:char
    +borrowTime:datetime
    +select()
    +update()
    +delete()
    +pay()
    +bookTimeCheck()
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
    +pay()
}
class 读者信息{
    +readerId:Interger 
    +readerName:String 
    +lendBookTime:String 
    +returnBookTime:String
    +select()
    +borrow()
    +addbook()
    +feedback()
    +findBook()
}
class 图书信息{
    +bookId:Interger
    +bookISBN:String
    +bookName:String 
    +total:Interger 
    +publisher:String 
    +author:String 
    +summary:String
    +bookinfo()
    +select()
    +delete()
    +update()
    +feedback()
    +pay()
}

借阅信息 -right-* 图书信息
管理员信息  --|>  读者信息  :mange
超级管理员  --*  管理员信息
超级管理员 --|> 图书信息
读者信息    <|--    注册用户
读者信息    <|--    会员
读者信息 <|-- 借阅信息
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
    mangerId：007
    mangerName:"Tom"
    mangerNumber：23
    mangeraAdress："science and information college"
    mangerPhone：1241255262
}
object 普通管理员{
    mangerId：0107
    mangerName:"Cathelin"
    mangerNumber：23
    mangerAdress："science_and_information_college"
    mangerPhone：1255552622
}
object 读者{
    readerId:s111
    readerName:"Alice"
    lendBooktime:18-5-1
    returntime：18-5-12
}
object 注册用户{
    id:b111
    name："小红"
    sex:"fm"
    role：0
    number 2
}
object 会员用户{
    id:b222
    name："小李"
    sex:"m"
    role：a1
    nunber：20
}
object 借书记录{
    borrowid:003
    bookid:a22
    readerid:b111
    borrowtime：18-2-5
}
object 图书信息{
    bookid:s12314
    bookName："《时间简史》"
    bookISBN：159-456-763-5612
    author："史蒂芬·霍金"
    publisher："成都大学出版社"
    total:50
    summary:"著名物理学家史提芬霍金所著"
}
超级管理员信息 --* 普通管理员:管理
普通管理员 --|> 读者
借书记录 -right-* 图书信息
读者 <|-- 借书记录
超级管理员信息 --|> 图书信息
读者 <|-- 注册用户
读者 <|-- 会员用户
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
    +publisher:String 
    +author:String 
    +summary:String
    ..getter..
    +getBookId()
    +getBookISBN()
    +getBookName()
    +getTotal()
    +getPublisher()
    +getAuthor()
    +getSummary()
    ..setter..
    +setBookId()
    +setBookISBN()
    +setBookName()
    +setTotal()
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
    +lendBookTime:String 
    +returnBookTime:String
    ..getter..
    +getReaderId()
    +getReaderName()
    +getLendBookTime()
    +getReturnBookTime()
    ..setter..
    +setReaderId()
    +setReaderName()
    +setLendBookTime()
    +setReturnBookTime() 
}
@enduml

```
### 3.3.1图片

![](./test3_5.png '描述')