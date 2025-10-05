# SpringMVC + MyBatis + ExtJS 权限管理系统

## 项目简介

这是一个基于Spring MVC、MyBatis和ExtJS技术栈开发的企业级权限管理系统平台。项目采用经典的SSM（Spring + SpringMVC + MyBatis）框架，前端使用ExtJS构建富客户端界面，实现了用户、角色、模块、权限等核心功能的完整管理。

## 技术栈

### 后端技术
- **Spring Framework 3.1.0**: IoC容器和AOP框架
- **Spring MVC 3.1.0**: MVC Web框架
- **MyBatis 3.0.6**: ORM持久层框架
- **MyBatis-Spring 1.0.2**: MyBatis与Spring集成
- **Apache Shiro 1.1.0**: 安全认证和授权框架

### 前端技术
- **ExtJS**: 企业级JavaScript框架
- **HTML/CSS/JavaScript**: 前端基础技术

### 数据库
- **MySQL**: 关系型数据库
- **BoneCP**: 高性能数据库连接池

### 构建工具
- **Maven**: 项目构建和依赖管理
- **Java 1.6+**: JDK版本

### 其他技术
- **Jackson 1.9.3**: JSON数据处理
- **SLF4J + Logback**: 日志框架
- **JUnit 4.8.2**: 单元测试
- **EasyMock 3.1**: Mock测试框架

## 功能特性

### 1. 用户管理
- 用户的增删改查
- 用户信息维护
- 用户状态管理
- 用户角色分配

### 2. 角色管理
- 角色的创建、编辑、删除
- 角色权限分配
- 角色与用户关联
- 角色与模块关联

### 3. 模块管理
- 系统模块配置
- 模块权限设置
- 模块树形结构管理
- 菜单权限控制

### 4. 权限管理
- 基于角色的访问控制(RBAC)
- 细粒度权限控制
- 字段级权限管理
- 动态权限验证

### 5. 系统功能
- 用户登录/登出
- 验证码验证
- 文件上传
- 国际化支持
- 拦截器权限控制

## 项目结构

```
springmvc-mybatis-extjs/
├── pom.xml                           # Maven项目配置文件
├── src/
│   ├── main/
│   │   ├── java/                     # Java源代码
│   │   │   └── com/chenxin/authority/
│   │   │       ├── web/              # Web层
│   │   │       │   ├── controller/   # 控制器
│   │   │       │   │   ├── UserController.java      # 用户控制器
│   │   │       │   │   ├── RoleController.java      # 角色控制器
│   │   │       │   │   ├── ModuleController.java    # 模块控制器
│   │   │       │   │   ├── FieldController.java     # 字段控制器
│   │   │       │   │   ├── LoginController.java     # 登录控制器
│   │   │       │   │   └── ...
│   │   │       │   ├── interseptor/  # 拦截器
│   │   │       │   │   └── LoginInterceptor.java    # 登录拦截器
│   │   │       │   └── listener/     # 监听器
│   │   │       │       └── SystemInitListener.java  # 系统初始化
│   │   │       ├── service/          # 服务层
│   │   │       ├── dao/              # 数据访问层(MyBatis Mapper)
│   │   │       │   ├── BaseUsersMapper.java
│   │   │       │   ├── BaseRolesMapper.java
│   │   │       │   ├── BaseModulesMapper.java
│   │   │       │   └── ...
│   │   │       └── entity/           # 实体类
│   │   ├── resources/                # 配置文件
│   │   │   ├── config/               # Spring配置
│   │   │   │   ├── spring/
│   │   │   │   │   ├── springmvc-servlet.xml    # SpringMVC配置
│   │   │   │   │   └── spring-pool.xml          # 数据源配置
│   │   │   │   ├── ibatis/
│   │   │   │   │   ├── mybatis-config.xml       # MyBatis配置
│   │   │   │   │   └── jdbc.properties          # 数据库连接配置
│   │   │   │   └── others/
│   │   │   │       ├── config.properties        # 系统配置
│   │   │   │       └── messages*.properties     # 国际化资源
│   │   │   ├── sqlmap/               # MyBatis SQL映射文件
│   │   │   │   ├── BaseUsersMapper.xml
│   │   │   │   ├── BaseRolesMapper.xml
│   │   │   │   └── ...
│   │   │   └── logback.xml           # 日志配置
│   │   └── webapp/                   # Web资源
│   │       ├── WEB-INF/
│   │       │   ├── web.xml           # Web应用配置
│   │       │   └── views/            # JSP视图
│   │       └── resources/            # 静态资源
│   │           ├── css/              # 样式文件
│   │           ├── images/           # 图片资源
│   │           └── js/               # JavaScript文件
│   └── test/                         # 测试代码
│       └── java/
│           └── com/chenxin/authority/
│               ├── controller/       # 控制器测试
│               └── service/          # 服务层测试
└── .springBeans                      # Spring IDE配置
```

## 依赖要求

### 运行环境
- **JDK**: 1.6 或以上
- **Maven**: 3.0+
- **MySQL**: 5.5+
- **Web容器**: Tomcat 7.0+ / Jetty / 其他Java EE容器

### 开发工具（可选）
- Eclipse / IntelliJ IDEA
- MySQL Workbench / Navicat
- Postman（API测试）

## 安装和运行方法

### 1. 环境准备

```bash
# 检查Java环境
java -version

# 检查Maven环境
mvn -version

# 确保MySQL服务已启动
mysql --version
```

### 2. 数据库配置

```bash
# 创建数据库
mysql -u root -p
CREATE DATABASE authority DEFAULT CHARACTER SET utf8;

# 导入数据库脚本（如果有提供）
# mysql -u root -p authority < database.sql

# 修改数据库连接配置
# 编辑 src/main/resources/config/ibatis/jdbc.properties
```

**jdbc.properties 配置示例：**
```properties
jdbc.driverClassName=com.mysql.jdbc.Driver
jdbc.url=jdbc:mysql://localhost:3306/authority?useUnicode=true&characterEncoding=UTF-8
jdbc.username=root
jdbc.password=your_password
```

### 3. 编译项目

```bash
# 进入项目目录
cd springmvc-mybatis-extjs

# Maven编译
mvn clean compile

# 打包
mvn clean package
```

### 4. 部署运行

**方式一：使用Maven Tomcat插件**
```bash
# 添加Tomcat插件配置到pom.xml后
mvn tomcat7:run

# 访问地址
http://localhost:8080/authority
```

**方式二：部署到Tomcat**
```bash
# 将target目录下的war包复制到Tomcat的webapps目录
cp target/authority-1.0.0.war $TOMCAT_HOME/webapps/

# 启动Tomcat
$TOMCAT_HOME/bin/startup.sh

# 访问地址
http://localhost:8080/authority-1.0.0/
```

**方式三：在IDE中运行**
1. 导入Maven项目到Eclipse/IDEA
2. 配置Tomcat服务器
3. 部署项目并启动
4. 访问应用

### 5. 访问系统

```
# 默认访问地址
http://localhost:8080/authority

# 登录页面
http://localhost:8080/authority/login

# 默认账号（需要查看数据库初始化脚本）
用户名: admin
密码: admin123
```

## 主要文件/模块说明

### 核心配置文件

#### pom.xml
- Maven项目对象模型文件
- 定义项目依赖和构建配置
- 包含Spring、MyBatis、Shiro等核心依赖

#### web.xml
- Web应用配置文件
- 配置Spring容器初始化
- 配置DispatcherServlet
- 配置字符编码过滤器

#### springmvc-servlet.xml
- SpringMVC核心配置
- 组件扫描配置
- 视图解析器配置
- 拦截器配置
- JSON转换器配置

#### mybatis-config.xml
- MyBatis全局配置
- 类型别名配置
- 插件配置
- 映射器配置

### 核心控制器

#### LoginController
- 用户登录/登出
- 验证码生成
- Session管理

#### UserController
- 用户CRUD操作
- 用户角色分配
- 用户数据导出

#### RoleController
- 角色管理
- 角色权限配置
- 角色用户关联

#### ModuleController
- 模块管理
- 权限配置
- 菜单树构建

### 拦截器

#### LoginInterceptor
- 登录状态验证
- 权限检查
- 请求拦截

### 数据访问层

MyBatis Mapper接口和XML映射文件：
- BaseUsersMapper: 用户数据操作
- BaseRolesMapper: 角色数据操作
- BaseModulesMapper: 模块数据操作
- BaseFieldsMapper: 字段权限操作

## 架构设计说明

### 三层架构
1. **表现层(Web Layer)**: SpringMVC控制器处理HTTP请求
2. **业务层(Service Layer)**: 业务逻辑处理，事务管理
3. **持久层(DAO Layer)**: MyBatis数据访问

### 权限控制
- 基于Apache Shiro的安全框架
- RBAC权限模型
- 拦截器实现权限验证
- 支持细粒度的字段级权限

### 前后端交互
- RESTful API设计
- JSON数据格式
- ExtJS前端组件

## 其他相关信息

### 开发规范
- Controller负责请求处理和响应
- Service处理业务逻辑
- Mapper只做数据访问
- 使用@Transactional进行事务管理

### 日志配置
- 使用SLF4J + Logback
- 日志级别可在logback.xml中配置
- 支持控制台和文件输出

### 性能优化
- BoneCP高性能连接池
- MyBatis二级缓存
- 延迟加载配置
- 合理使用索引

### 安全建议
1. 修改默认管理员密码
2. 配置HTTPS访问
3. 启用CSRF防护
4. 定期更新依赖版本
5. 数据库连接信息加密

### 扩展功能建议
- 添加日志审计功能
- 集成单点登录(SSO)
- 增加数据权限控制
- 实现API接口文档
- 添加监控和性能分析

### 注意事项
- 项目使用较旧版本的框架，建议升级到最新稳定版
- Spring 3.1、MyBatis 3.0已有新版本
- 注意SQL注入和XSS攻击防护
- 生产环境需要调整日志级别和性能参数