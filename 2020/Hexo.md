### 个人博客搭建（github + nodejs + hexo + theme (3-Hexo)）：

#### 1.git 下载与安装
##### git 简介：

Git (/ɡɪt/)is a distributed version-control system（分布式版本控制系统） for tracking changes in source code during software development.It is designed for coordinating work among programmers, but it can be used to track changes in any set of files. Its goals include speed, data integrity, and support for distributed, non-linear workflows[clarification needed].

The reasons why we use **git**
![](https://www.google.com/imgres?imgurl=https%3A%2F%2Fwww.nobledesktop.com%2Fimage%2Fblog%2Fgit-branches-merge.png&imgrefurl=https%3A%2F%2Fwww.nobledesktop.com%2Fblog%2Fwhat-is-git-and-why-should-you-use-it&tbnid=RuCur-BGF1IeWM&vet=12ahUKEwiNieac4Z_sAhUHa5QKHZi8D6MQMygkegUIARCZAg..i&docid=fN9btghZUqB8kM&w=968&h=496&q=git&ved=2ahUKEwiNieac4Z_sAhUHa5QKHZi8D6MQMygkegUIARCZAg)


##### git 下载与安装：

you can download ： [website](https://git-scm.com/downloads)

the installtion just follows the defalut.


##### git 使用：

git 中文教程: [廖雪峰git 教程](https://www.liaoxuefeng.com/wiki/896043488029600)


#### 2.Nodejs 下载与安装
##### nodejs [简介：](https://nodejs.org/en/about/)

As an **asynchronous event-driven JavaScript runtime**, Node.js is designed to **build scalable network applications**. In the following "hello world" example, many connections can be handled concurrently. Upon each connection, the callback is fired, but if there is no work to be done, Node.js will sleep.


```javascript


const http = require('http');

const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World');
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});

```


##### nodejs 下载与安装：

根据操作系统选择相应 'source code' 或者 'pre-built installer'
安装过程保持默认设置即可

##### nodejs 使用：

官方手册 [documentation](https://nodejs.org/dist/latest-v12.x/docs/api/)

#### 3.Hexo 下载与安装
##### Hexo [简介：](https://hexo.io/docs/)

Hexo is a fast, simple and powerful blog framework. You write posts in Markdown (or other markup languages) and Hexo generates static files with a beautiful theme in seconds.

##### Hexo 下载与安装： 

###### 3.1. 命令行安装 

```
npm install hexo-cli -g

```

windows 系统可能出现报错： `win32 不支持 fsevents` ， SKIPPING OPTIONAL DEPENDENCY， 不影响 hexo 基本功能 	
[json optional dependencies](https://docs.npmjs.com/files/package.json#optionaldependencies) 

```
WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@~2.1.2 (node_modules\hexo-cli\node_modules\chokidar\node_module
s\fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@2.1.3: wanted {"os":"darwin","arch":"any
"} (current: {"os":"win32","arch":"x64"})
```

###### 3.2.检查 hexo 是否已经安装成功：

```
hexo version
```
```
hexo-cli: 4.2.0
os: Windows_NT
node: 12.18.4
v8: 7.8.279.23-
uv: 1.38.0
zlib: 1.2.11
brotli: 1.0.7
ares: 1.16.0
modules: 72
nghttp2: 1.41.0
napi: 6
llhttp: 2.1.2
http_parser: 2.
openssl: 1.1.1g
cldr: 37.0
icu: 67.1
tz: 2019c
unicode: 13.0
```
###### 3.3.初始化(文件克隆 hexo-starter、Submodule themes/landscape、；安装依赖)

```
hexo init username.github.io
```

初始化成功提醒：

```
INFO  Start blogging with Hexo!
```

###### 3.4.测试 本地服务 是否可以启动

```
 hexo server
```

server 成功提醒INFO ：

```
INFO  Validating config
INFO  Start processing
INFO  Hexo is running at http://localhost:4000 . Press Ctrl+C to stop.
INFO  Bye!
```

###### 3.5. 生成 SSH Keys, 并添加至 github, 测试 本地与 github 通信是否成功

```
 ssh-keygen -t rsa -C "***@***.com"
```

KEY 添加方法 ： Github --> settings --->  SSH keys setting 

通信测试 ： 

```
ssh -T git@github.com
```

```
Hi ***! You've successfully authenticated, but GitHub does not provide shell access.
```

or

```
$ ssh git@github.com
```

```
Hi ******! You've successfully authenticated, but GitHub does not provide shell access.
Connection to github.com closed.
```

###### 3.6. 配置 SSH 服务 、`_config.yml`文件  ： 如未配置，则每次 `hexo deploy` 均需要输入用户名及密码:

```
$ git config --global user.name "******"// github用户名
$ git config --global user.email  "******"// github注册邮箱
```

`_config.yml`文件更改为：
```
deploy:
  type: git
  repository: git@github.com:username/username.github.io.git
  branch: master
```

不当写法：此种写法为 `hexo2.*` 版本书写规则，执行 `hexo d` 时会导致报错 `Deployer not found: github or Deployer not found: git
` , 可通过安装插件解决 `npm install hexo-deployer-git --save`

```
deploy:
  type: github
  repository: https://github.com/username/username.github.io.git
  branch: master
```

##### 4. 域名解析：

添加域名解析后，可使个性化域名指向博客 。 
为域名添加两条记录：
主机记录（@ ; www）; 记录类型（A ; CNAME）; 解析线路 （默认 ; 默认） ； 记录值 （ IP ； ***.github.io） ; TTL (10min ;10min)

IP 获取方式 ： 

```
ping ***.github.com  
```




##### 5. Hexo 使用教程（主题更换）：

[官方教程](https://hexo.io/docs/)
[3-hexo yelog](https://yelog.org/2017/03/23/3-hexo-instruction/)





