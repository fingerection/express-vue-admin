# express-vue-admin

### 使用Node.js（Express）, Vue2开发的管理后台脚手架项目

#### 前后端分离，后端提供REST API，前端是组件化的Web App；实现了后台项目最基本的用户/角色/权限管理等功能；

### 项目构成:

* [vue2](https://vuejs.org/) - 前端JS框架
* [iview](https://www.iviewui.com/) - 前端UI框架
* [vue-resource](https://github.com/pagekit/vue-resource)/[vue-router](https://github.com/vuejs/vue-router)/[vuex](https://github.com/vuejs/vuex) - 前端主要组件
* [express](https://expressjs.com/) - 后端web框架
* [sequelize](http://docs.sequelizejs.com/) - ORM
* [joi](https://github.com/hapijs/joi) - 参数校验
* [dotenv](https://github.com/motdotla/dotenv) - 环境配置
* [mocha](https://mochajs.org/)/[chai](http://chaijs.com/)/[chai-http](https://github.com/chaijs/chai-http) - 接口测试组件
* mysql - 数据库
* redis - 缓存
* ...


### 项目结构：

      .
      ├── .env.example  环境配置示例
      ├── .sequelizerc  sequelize配置
      ├── screenshots/  应用运行截图
      ├── web/          vue web应用
      ├── test/         接口测试文件
      ├── server.js     服务器
      ├── middleware/   中间件
      | ├── base.js     基础中间件
      | ├── auth.js     鉴权中间件
      | └── ...         其他业务中间件
      ├── route/        路由
      | ├── base.js     基础路由
      | ├── admin.js    admin模块路由
      | └── ...         其他路由
      ├── controller/   控制器
      | ├── base.js     基础控制器
      | ├── rest.js     rest基础控制器
      | ├── session.js  session控制器
      | ├── admin/      admin模块控制器
      | └── ...         其他业务模块控制器
      ├── database/     sequelize数据库文件
      | ├── models/     模型
      | └── migrations/ migration文件
      | └── seeders/    seeder文件
      ├── util.js       工具
      └── config/       配置
        └── database.js sequelize-cli数据库配置

### 运行截图:

#### login

<p align="center">
<kbd>
  <img src="https://raw.github.com/jarontai/express-vue-admin/master/screenshots/login.png">
</kbd>
</p>

#### admin/user

<p align="center">
<kbd>
  <img src="https://raw.github.com/jarontai/express-vue-admin/master/screenshots/admin_user.png">
</kbd>
</p>

#### admin/role

<p align="center">
<kbd>
  <img src="https://raw.github.com/jarontai/express-vue-admin/master/screenshots/admin_role.png">
</kbd>
</p>

#### admin/role delete

<p align="center">
<kbd>
  <img src="https://raw.github.com/jarontai/express-vue-admin/master/screenshots/admin_role_delete.png">
</kbd>
</p>


### 运行:

 0. 安装redis，用于存储session

 1. 复制.env.example到.env，并对各个项目进行配置
    ```
    #server
    NODE_ENV=development 环境配置
    SERVER_PORT=3000 服务器端口
    API_PATH=/api 接口基路径
    API_VERSION=v1 接口版本

    #db
    DB_HOST=localhost 数据库host
    DB_DATABASE=admin 数据库名称
    DB_USER=root 数据库用户
    DB_PASSWORD=root 数据库密码

    #redis
    REDIS_HOST=localhost redis缓存host
    REDIS_PORT=6379 redis端口

    #misc
    ADMIN_SEED_PASSWORD=adminpwd admin帐号密码
    TEST_SEED_PASSWORD=testpwd 测试帐号密码
    SERVER_PORT_TEST=3001 单元测试服务器端口

    ```
 2. 全局安装sequelize-cli
    ```
    $ npm install -g sequelize-cli
    ```
 3. 安装依赖、初始化数据库、填充seed数据:
    ```
    $ npm install // 安装依赖
    $ sequelize db:migrate // 数据库结构构建
    $ sequelize db:seed:all // 数据库数据填充
    ```
 4. 运行server和web应用
    ```
    $ npm start // 开启后端服务

    $ cd ./web  // 进入web文件夹
    $ npm install // 安装依赖
    $ npm run dev // 运行web应用
    ```

### Test
```
$ npm run test
```

### TODO

* 使用[node_acl](https://github.com/OptimalBits/node_acl)优化重构权限逻辑
* 优化角色权限管理等表单的UI
* 后台耗时操作（如修改密码）的loading提示
* 国际化（i18n）
* 更多的测试代码
* ...
