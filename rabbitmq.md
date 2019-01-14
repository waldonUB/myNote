### rabbitmq简要安装教程
1.首先，您需要安装支持的 Windows 版Erlang。下载并运行Erlang for Windows 安装程序。
2.运行RabbitMQ安装程序rabbitmq-server-3.7.3.exe
3.该服务将使用其默认设置正常运行。你可以自定义RabbitMQ环境或编辑配置。 
 (1)erl环境变量配置(注意文件夹不要有中午和空格)  `ERLANG_HOME=C:\develop\erl9.2`
 (2)在path加入 `%ERLANG_HOME%\bin`
 (3) 测试erl配置是否正确，开始-运行-cmd，输入erl，显示如下，证明配置正确 
4. RabbitMQ环境变量配置 
 (1)`RABBITMQ_SERVER=C:\develop\rabbitmq_server-3.7.3`
 (2) 在Path中加入 `%RABBITMQ_SERVER%\sbin`
 (3)在sbin目录下输入`./ rabbitmq-plugins.bat enable rabbitmq_management`
 (4) `net start RabbitMQ` 启动mq (需注意当前账号有无管理员权限,无则右键win打开管理员命令提示符)
 (5)关闭`mq net stop RabbitMQ`
5.测试mq
测试地址 http://localhost:15672/ 
默认的用户名：guest 
默认的密码为：guest
