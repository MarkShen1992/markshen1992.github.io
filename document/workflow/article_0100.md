### 工作流相关内容

---

工作流总是以**任务的形式驱动人处理业务或者驱动业务系统自动完成作业**。有了工作流引擎之后，我们不必一直等待其他人的工作进度，直白地说，我们只需要关心系统首页的代办任务数即可，由系统提醒当前有多少待办任务需要处理。

#### Activiti架构

![Activiti架构](<http://www.myexception.cn/img/2012/10/15/094950133.jpg>)



#### 七大接口

- RepositoryService: 流程仓库，用户管理流程仓库，例如，部署，删除，读取流程资源
- TaskService: 任务，用户管理，查询任务，例如，牵手，办理，指派等
- IdentityService: 身份，可以管理和查询用户，组之间的关系
- FormService: 表单，用户读取和流程，任务相关的表单数据
- RuntimeService: 运行时，可以处理所有正在运行状态的流程实例，任务等
- ManagementService: 引擎管理，和具体业务无关，主要可以查询引擎配置，数据库，作业等
- HistoryService: 历史，可以查询所有历史数据，例如，流程实例，任务，活动，变量，附件等

#### 应用

- 系统集成
  - 与**ESB**整合
  - 与规则引擎整合，**JBoss Drools**
  - 嵌入已有系统平台
- 其他产品

#### 生命周期

![工作流生命周期](<http://www.uml.org.cn/soa/images/2016031111.jpg>)

**Talk is cheap, show me the code!!!**



#### Activiti学习资料

[Business Process Model and Notation](<http://www.bpmn.org/>)

[咖啡兔博客](<http://www.kafeitu.me/>)

[Activiti实战源码](<https://github.com/henryyan/activiti-in-action-codes>)

[activiti官网](<https://www.activiti.org/>)  [activiti官网文档6.0](<https://www.activiti.org/userguide/>)

工作流学习笔记<https://blog.csdn.net/evan_leung/article/details/51589870>

![工作流学习笔记](<https://img-blog.csdn.net/20160605224959812>)

----

[back2index](./../../index.html)