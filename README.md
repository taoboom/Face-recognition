### 基于springboot的人脸识别项目
#### 邮箱
2024920793@qq.com

#### 前期准备

1、注册虹软sdk 获取appid  sk 

2、注册阿里云对象存储，创建bucket

#### 前端配置部署  

前端共分为两个项目  

face-web为人脸识别人脸库管理后台  

```shell
npm install  --安装依赖
npm run dev --启动项目
```

face-get 为调用人脸识别的前台

```shell
npm install --安装依赖
npm run serve -- 启动项目
```

#### 后端配置

后端分为四个模块  

common为公共类无需修改  

eurake为微服务模块无需修改  

face_corn为人脸识别核心模块，需要修改的配置有 

```yml
redis: -- redis配置
    host: 127.0.0.1
    port: 6379
    password:
datasource:-- 数据库配置
    url: jdbc:mysql://localhost:3306/face_warehouse?serverTimezone=UTC&useUnicode=true&characterEncoding=utf8&useSSL=false&allowPublicKeyRetrieval=true
    username: root
    password: 123456 
 face: -- 虹软引擎存放地址及 appid sdkkey 
  dllPath: #存放引擎文件的地址
  appId: ''
  sdkKey: ''

```

face_warehouse 为人脸库管理模块及微服务调用模块，需要修改的配置有  

```yml
datasource: -- 数据源
    url: jdbc:mysql://localhost:3306/face_warehouse?serverTimezone=UTC&useUnicode=true&characterEncoding=utf8&useSSL=false&allowPublicKeyRetrieval=true
    username: root
    password: 123456
```

#### 项目启动 

依次启动eurake-face_corn-face_warehouse


