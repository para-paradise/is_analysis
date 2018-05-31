<!-- markdownlint-disable MD033-->
<!-- 禁止MD033类型的警告 https://www.npmjs.com/package/markdownlint -->

# 接口：getOneStudentResults  [返回](../README.md)
用例： [查看成绩](../用例/查看成绩.md)，[评定成绩](../用例/评定成绩.md)

- 功能：
    返回一个学生的所有实验成绩和实验评价。
    
- 权限：
    学生：只能查看自己的成绩，即接口参数student_id必须等于登录学生的student_id
    老师：可以查看所有学生的成绩。
    
- API请求地址： 
    接口基本地址/v1/api/getOneStudentResults/<student_id&collage_name&course_name>

- 请求方式 ：
    GET

- 请求参数说明:        

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |student_id|学生的学号|
  |collage_name|院系专业|
  |course_name|课程名|
- 返回实例：

        {         
            "status": true,
            "info": null,  
            "collage_name":"信息科学与工程学院--软件工程"  
            "course_name":"java"
            "student_id": "201510315203", 
            "github_username": "chinajuedui", 
            "class": "软件(本)15-1", 
            "name": "陈松华", 
            "total": 6,
            "avgresult":90.5,       
            "data": [
                {
                "test_id":1,
                "web_exists": true, 
                "standard":
                    "1.实验完整性（满分20)","14",
                    "2.根据实验实际上课的内容正确、完整地写出实验目的（满分20）","18",
                    "3.对比实验目的撰写实验原理。必须有相应的原理图或方案框图并对之进行简单说明，给出实验中涉及的相关公式。要求叙述完整、言简意赅。（满分20）","10",
                "result": 10, 
                "memo":"本实验做得好",
                "update_date": "2018-04-02 13:48:01"
                }, 
                {
                ...其他实验
                }
            ] 
        }
 
- 返回参数说明：    
 
  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |status|bool类型，true表示正确的返回，false表示有错误|
  |info|返回结果说明信息|
  |collage_name|返回学院专业信息|
  |course_name|返回课程信息|
  |student_id|学号|
  |github_username|学生的gitHub用户名|
  |class|班级|
  |name|真实姓名|   
  |total|实验总数|
  |avgresult|实验平均成绩|   
  |data|所有实验的成绩和评语|
  |test_id|实验编号|
  |web_exists|本实验的GitHub网页是否存在|
  |standard|本实验的细节评分标准，分数可以为0|
  |result|本实验成绩，可以为空，为空表示没有批改，没有批改的实验不入平均成绩，为0分则要计入平均成绩，所以成绩为空和为0是不一样的。|
  |memo|本实验老师的评价，可以为空|
  |update_date|本实验老师的批改日期，可以为空|


