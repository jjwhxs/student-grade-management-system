### 系统介绍

基于SpringBoot和Vue实现的学生成绩管理系统采用前后端分离的架构方式，系统设计了三种角色，分别是学生、教师、管理员，每种角色拥有不同的菜单权限，学生可以在系统中进行系统登录、主页、课程表、成绩查询、成绩详情、个人中心等功能模块的操作，教师可以在系统中进行系统登录、主页、课程表、成绩查询、成绩详情、个人中心等功能模块的操作，管理员可以在系统中进行系统登录、主页、课程表、成绩查询、成绩详情、课程录入、用户管理、账号管理、个人中心等功能模块的操作。

### 技术选型

开发工具：idea2020.3+webstorm2020.3

运行环境：jdk1.8+maven3.6.3+mysql5.7+nodejs12.19.0

服务端技术：springboot+mybatis+fastjson+pagehelper

前端技术：html+css+vue+axios+element-ui+echarts

### 成果展示

系统登录
<img width="1910" height="1045" alt="系统登录" src="https://github.com/user-attachments/assets/9da4147b-1e21-4277-9336-070e2d9812e5" />

系统主页
<img width="1910" height="1045" alt="系统主页" src="https://github.com/user-attachments/assets/12956b15-01ea-48d1-9307-9ed1e3f95751" />

课程表
<img width="1910" height="1045" alt="课程表" src="https://github.com/user-attachments/assets/ab30ae5b-ad8e-48b9-8dd9-76127e014095" />

成绩查询
<img width="1910" height="1045" alt="成绩查询" src="https://github.com/user-attachments/assets/bf13f1e6-e6ec-4fe0-8758-0b37cd1686ad" />

成绩详情
<img width="1910" height="1045" alt="成绩详情" src="https://github.com/user-attachments/assets/bce3278c-9027-4c83-ad2e-2a04bbf3db84" />

课程录入
<img width="1910" height="1045" alt="课程录入" src="https://github.com/user-attachments/assets/278fc3f7-8089-458d-9d37-b7d6961bf6dd" />

用户管理->学生用户
<img width="1910" height="1045" alt="用户管理-学生用户" src="https://github.com/user-attachments/assets/7a397612-cbf1-4bc6-9bf8-5c7a37703dde" />

账号管理
<img width="1910" height="1045" alt="账号管理" src="https://github.com/user-attachments/assets/5e5898bb-b708-468c-a4c3-8d964d9cf78b" />

### 源码展示

@RestController

@RequestMapping("/api/sms/score")

public class ScoreController {

@Autowired

private ScoreService scoreService;

@GetMapping("/getCourseList")

public PagingResult<Course> getCourseList(@RequestParam Map<String, Object> condition,
                                          @RequestParam(required = false, name = "$limit", defaultValue = "10") Integer limit,
                                          @RequestParam(required = false, name = "$offset", defaultValue = "0") Integer offset) {
                                          
    RowBounds rowBounds = new RowBounds(offset, limit);
    return scoreService.getCourseList(rowBounds, condition);
    
}

@PostMapping

private void addEntry(@RequestBody JSONArray UserScore) {

    List<Score> list = JSONObject.parseArray(UserScore.toJSONString(), Score.class);
    scoreService.addEntry(list);
    
}

@GetMapping("/export")

public List<Course> getExportList(@RequestParam Map<String, Object> condition) {

    return scoreService.getExportList(condition);
    
}

@GetMapping("/getUserNum")

public List<Map<String, Object>> getUserNum(@RequestParam Map<String, Object> condition) {

    return scoreService.getUserNum(condition);
    
}

@GetMapping("/getUserTotal")

public Map<String, Object> getUserTotal(@RequestParam Map<String, Object> condition) {

    return scoreService.getUserTotal(condition);
    
}

}

### 账号地址及其它说明

1、地址说明

登录页：localhost:9122

2、账号说明

学生：3168901101/123456

教师：3890290/159357

管理员：root/password

3、目录结构展示

<img width="704" height="177" alt="目录结构展示" src="https://github.com/user-attachments/assets/b525cfee-211f-4f69-a903-8dcbdfaf12b2" />

4、项目结构展示

<img width="1706" height="764" alt="项目结构展示" src="https://github.com/user-attachments/assets/10f405a2-8050-4d7c-8673-4a6b825a0e2a" />

5、运行步骤

1）创建数据库、导入sql脚本

2）修改application.properties中的数据库配置文件，启动服务端

3）在StudentManagerSystemVue目录下打开cmd，执行npm install下载依赖

4）下载完毕后启动前端npm run serve，访问端口

### 获取方式(可远程调试)

访问链接(在浏览器中手动输入下图中的地址)：

<img width="1049" height="119" alt="链接" src="https://github.com/user-attachments/assets/cfe4ce39-c23c-4743-a06c-77a5c09e69f3" />

若资源获取失败，可添加happy35596339(vx)或2061772307(qq)进行交流
