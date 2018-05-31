# 基于GitHub的实验管理平台的分析与设计

|学号|班级|姓名|
|:----:|:----:|:----:|
|201510414118|15级软工一班|任翔|

## 1.概述

* 基于GitHub的实验管理平台的作用是在线管理实验成绩的Web应用系统。学生和老师的实验内容均存放在GitHUB 页面上。
* 学生的功能主要有：一是设置自己的GitHub用户名，二是查询自己的实验成绩，查询课程。学生的GitHub用户名是公开的，但成绩不公开。
* 老师的功能主要有：一是批改每个学生的成绩，二是查看每个学生的成绩，三是查看课程，四是发布课程，五是查看实验，六是发布实验。
* 老师和学生都能通过本系统的链接方便地跳转到学生的每个GitHUB实验目录，以便批改实验或者查看实验情况。
* 实验成绩按数字分数计算，每项实验的满分为100分，最低为0分。
* 系统自动计算每个学生的所有实验的平均分和总分。

## 2.系统总体结构
![](./系统总体结构.png '描述')
界面设计参见： https://para-paradise.github.io/is_analysis/test6/ui/index.html
## 3.用例设计 [源码](./src/用例设计.puml)
![](./out/src/用例设计/用例设计.png '描述')
## 4.类图设计 [源码](./src/类图设计.puml)
![](./out/src/类图设计/类图设计.png '描述')
## 5.数据库设计
* ## [参考数据库设计](./src/数据库设计.md)
## 6.用例及界面详细设计
* ### [“学生列表”用例](./用例/学生列表.md)，[界面](https://para-paradise.github.io/is_analysis/test6/ui/index.html)
* ### [“登录”用例](./用例/登录.md)，[界面](https://para-paradise.github.io/is_analysis/test6/ui/%E7%99%BB%E5%BD%95.html)
* ### [“登出”用例](./用例/登出.md)，[界面](https://para-paradise.github.io/is_analysis/test6/ui/%E9%A1%B6%E9%83%A8%E8%8F%9C%E5%8D%95.html)
* ### [“修改密码”用例](./用例/修改密码.md)，[界面](https://para-paradise.github.io/is_analysis/test6/ui/%E4%BF%AE%E6%94%B9%E5%AF%86%E7%A0%81.html)
* ### [“查看用户信息”用例](./用例/查看用户信息.md)，[界面](https://para-paradise.github.io/is_analysis/test6/ui/%E6%9F%A5%E7%9C%8B%E7%94%A8%E6%88%B7%E4%BF%A1%E6%81%AF.html)
* ### [“修改用户信息”用例](./用例/修改用户信息.md)，[界面](https://para-paradise.github.io/is_analysis/test6/ui/%E4%BF%AE%E6%94%B9%E7%94%A8%E6%88%B7%E4%BF%A1%E6%81%AF.html)
* ### [“查看成绩”用例](./用例/查看成绩.md)，[界面](https://para-paradise.github.io/is_analysis/test6/ui/%E6%88%90%E7%BB%A9%E6%9F%A5%E8%AF%A2.html)
* ### [“评定成绩”用例](./用例/评定成绩.md)，[界面](https://para-paradise.github.io/is_analysis/test6/ui/%E6%88%90%E7%BB%A9%E8%AF%84%E5%AE%9A.html)
* ### [“查看实验”用例](./用例/查看实验.md)，[界面](https://para-paradise.github.io/is_analysis/test6/ui/%E5%AE%9E%E9%AA%8C%E6%9F%A5%E7%9C%8B.html)
* ### [“发布实验”用例](./用例/发布实验.md)，[界面](https://para-paradise.github.io/is_analysis/test6/ui/%E5%8F%91%E5%B8%83%E5%AE%9E%E9%AA%8C.html)
* ### [“查看课程”用例](./用例/查看课程.md)，[界面](https://para-paradise.github.io/is_analysis/test6/ui/%E8%AF%BE%E7%A8%8B%E4%BF%A1%E6%81%AF.html)
* ### [“发布课程”用例](./用例/发布课程.md)，[界面](https://para-paradise.github.io/is_analysis/test6/ui/%E5%8F%91%E5%B8%83%E8%AF%BE%E7%A8%8B.html)
