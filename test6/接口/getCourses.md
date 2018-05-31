<!-- markdownlint-disable MD033-->
<!-- 禁止MD033类型的警告 https://www.npmjs.com/package/markdownlint -->

# 接口：getCourses  [返回](../README.md)
用例：
    [评定成绩](../用例/评定成绩.md)
    [查看成绩](../用例/评定成绩.md)


- 功能：
    课程选择。
    
- 权限：
    学生/老师：修改自己的密码，必须先登录。    
    
- API请求地址： 
    接口基本地址/v1/api/getCollages/<course_id>

- 请求方式 ：
    GET

- 请求参数说明:        

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |course_id|课程编号| 
  
- 返回实例：

        {         
            "status": true,
            "info": null，
            "course_id":"#1",
            "course_name":"java",
            "summery":"java语言是最好的语言", 
            "number":"40",
            "teacher"_name:"刘老师",    
        }
 
- 返回参数说明：    
 
  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |status|bool类型，true表示正确的返回，false表示有错误|
  |info|返回结果说明信息|
  |course_id|课程编号| 
  |course_name|课程信息名字|
  |summery|简介|
  |number|人数|
  |teacher_name|教师姓名|

