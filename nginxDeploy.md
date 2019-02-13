#### windows版
1.在[nginx的官网](http://nginx.org/en/download.html)可以下载nginx,完了之后打开/nginx/conf/nginx.conf <br/>
2.找到http下的server

```
server {
        listen       80;
        server_name  localhost;

        #charset koi8-r;

        #access_log  logs/host.access.log  main;

        location /gc/ {
            proxy_pass   http://localhost:8080;
            root   html;
            index  index.html index.htm;
        }
    }
```
listen:当前启动的端口号<br/>
location:匹配要转发的路径<br/>
proxy_pass:要反向代理的路径<br/>
这里的写法和vue中的proxyTable有点类似,只不过vue中的代理
一般写在dev节点内
```
proxyTable: {  
'/api': {  target: 'http://localhost:8080', // 代理服务器路径  pathRewrite: {    '^/api': '/gc' // 重写路径  },  changeOrigin: true // 是否跨域}
},
```
所以还要在vue的配置文件内增加对生产还有开发环境的判断
```
// 判断是否服务器环境(测试/生产? 如何判断?)
const isProdMode = Object.is(process.env.NODE_ENV, 
'production')
module.exports = { baseURI: isProdMode ? 'gc/' : 'api/'}
```
3.nginx的常用命令<br/>
start nginx  启动nginx<br/>
./nginx.exe -s stop  停止nginx<br/>
./nginx.exe -s reload 重启nginx(可以热部署)<br/>
tip:如果发生404,请检查路径是否匹配得上,如果匹配不上将不会转发代理路径.
