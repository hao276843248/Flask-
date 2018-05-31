Flask
=====
Flask笔记
****
## 目录
* [Flask第一天](#Flask第一天)
    *  [Web应用程序的本质](#Web应用程序的本质)
    *  [Flask简介](#Flask简介)
    *  [Flask常用扩展包](#Flask常用扩展包)
    *  [Web框架](#Web框架)
    *  [虚拟环境](#虚拟环境)
        * [命令](#命令)
    * [其他相关介绍](#其他相关介绍)
    * [Flask程序实例](#Flask程序实例)
* [Flask第二天](#Flask第二天)
* [Flask第三天](#Flask第三天)
* [Flask第四天](#Flask第四天)
* [Flask第五天](#Flask第五天)
* [Flask第六天](#Flask第六天)
* [Flask第七天](#Flask第七天)

# Flask第一天
# Web应用程序的本质
>Web(World Wide Web)诞生最初的目的，是为了利用互联网交流工作文档。
# Flask简介
>Flask诞生于2010年，是Armin ronacher（人名）用 Python 语言基于 Werkzeug 工具箱编写的轻量级Web开发框架。
Flask 本身相当于一个内核，其他几乎所有的功能都要用到扩展（邮件扩展Flask-Mail，用户认证Flask-Login，数据库Flask-SQLAlchemy），都需要用第三方的扩展来实现。比如可以用 Flask 扩展加入ORM、窗体验证工具，文件上传、身份验证等。
>>Flask 没有默认使用的数据库，你可以选择 MySQL，也可以用 NoSQL。
>>>其 WSGI 工具箱采用 Werkzeug（路由模块），模板引擎则使用 Jinja2。这两个也是 Flask 框架的核心。
# Flask常用扩展包
* Flask-SQLalchemy：操作数据库；
* Flask-script：插入脚本；
* Flask-migrate：管理迁移数据库；
* Flask-Session：Session存储方式指定；
* Flask-WTF：表单；
* Flask-Mail：邮件；
* Flask-Bable：提供国际化和本地化支持，翻译；
* Flask-Login：认证用户状态；
* Flask-OpenID：认证；
* Flask-RESTful：开发REST API的工具；
* Flask-Bootstrap：集成前端Twitter Bootstrap框架；
* Flask-Moment：本地化日期和时间；
* Flask-Admin：简单而可扩展的管理接口的框架
* [扩展列表](http://flask.pocoo.org/extensions/)
* [中文文档](http://docs.jinkan.org/docs/flask/)
* [英文文档](http://flask.pocoo.org/docs/1.0/)
# Web框架
* 在 Python 中常用的 Web 框架有
    * flask
    * django
    * tornado
# Flask特点
* 简洁
* 轻巧
* 扩展性强
* 没有默认数据库
* 核心
    * WSGI工具箱
	>werkzeug 工具箱 封装了请求和响应以及路由
	* 模板引擎
    >Jinjia2
# 虚拟环境
## 命令
### 安装虚拟环境
>sudo pip install virtualenv <br>
sudo pip install virtualenvwrapper
#### 安装完虚拟环境后，如果提示找不到mkvirtualenv命令，须配置环境变量：
``` 
# 1、创建目录用来存放虚拟环境
mkdir 
$HOME/.virtualenvs

# 2、打开~/.bashrc文件，并添加如下：
export WORKON_HOME=$HOME/.virtualenvs
source /usr/local/bin/virtualenvwrapper.sh

# 3、运行
source ~/.bashrc
```
### 创建虚拟环境
>`mkvirtualenv -p python3 虚拟环境名称`（创建基于Python3的虚拟环境）<br>
```
例 ：
mkvirtualenv -p python3 py3_flask
```
>`mkvirtualenv 虚拟环境名称`（创建基于Python2的虚拟环境）
```
例 ：
mkvirtualenv py_flask
```
### 查看虚拟环境
>`workon`
### 使用虚拟环境
>`workon 虚拟环境名称`
### 退出虚拟环境
>`deactivate`
### 删除虚拟环境
>`rmvirtualenv 虚拟环境名称`
### 查看虚拟环境中安装的包 
>`pip list ` # 仅输出列表<br>
`pip freeze` # 按照所有版本号输出
### 安装相关包
* `pip install 包名称==版本号`
* 安装依赖文件
    >`pip install -r requirement.txt` 安装依赖包中的所有依赖文件
* 生成依赖文件
    >`pip freeze>requirements.txt` 生成当前虚拟环境的所有依赖文件
* 依赖包 项目所需要的扩展包
    >`pip install 项目所需要的扩展包`
### 作用
>**作用:**`虚拟环境`可以搭建独立的`python运行环境`, 使得单个项目的运行环境与其它项目互不影响.<br>
所有的虚拟环境都位于/home/下的隐藏目录.virtualenvs下
# 其他相关介绍
* url(统一资源定位符)
* 路由器网关默认网关的区别
	* 网关
		>不具体特指一类产品，只要连接两个不同的网络的设备都可以叫网关
	* 路由器
		>一般特指能够实现路由寻找和转发的特定类产品
* 路由能实现网关的功能
	* 默认网关
		>是一个网络层的概念PC本身不具备路由寻址能力，所以PC要把所有的IP包发送到一个默认的中转地址上面进行转发，也就是默认网关。<br>
		这个网关可以在路由器上，可以在三层交换机上，可以在防火墙上，可以在服务器上，所以和物理的设备无关。
* url地址? 问号后面是参数  key=value 形式&隔开
* 请求方法 `GET/POS/PUT/DELETE`等
* 通过并发推测用户数量
	>并发数100
	>>用户数1000
	>>>注册用户数10000
* 状态码code=
	* 1xx 临时响应
	* 2xx 成功
	* 3xx 重定向
	* 4xx请求错误
	* 5xx 服务器错误
	* 428 要求先决条件
	* 429 太多请求
	* 431 请求字段太大
# Flask程序实例
## 导入Flask
```py
from flask import Flask
```
## 创建Flask应用实例
>默认访问自定义的视图函数没有错误,	传入模块名,static会从响应模块名目录查找,	传入任意字符串会从当前目录下查找static
```py
app = Flask(__name__)
```
>`__del__`也叫析构方法执行垃圾回收
## 定义视图函数并绑定URL
```py
@app.route('/')
def index():
    return 'Hello World'
```
## 启动服务器
```py
if __name__ == '__main__':
    app.run()
```
# Flask第六天







