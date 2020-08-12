## SUKE/素客
关于本地服务器
如果您无法在真正的服务器上运行您的测试代码，
您可以选用使用Node.js来创建您的本地服务器以作测试
您需要先下载[Node.js](https://nodejs.org/zh-cn)以进行运行
当您的Node下载成为下界面时，就可以运行了。
![node.js](https://img-blog.csdnimg.cn/20200812163602241.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1OTg0NjY0,size_16,color_FFFFFF,t_70#pic_center)
您可以将以下文件拖入Node.js

```
sever.js
```

```javascript
var http = require('http');
var fs = require('fs');
var url = require('url');
 
 
// 创建服务器
http.createServer( function (request, response) {  
   // 解析请求，包括文件名
   var pathname = url.parse(request.url).pathname;
   
   // 输出请求的文件名
   console.log("Request for " + pathname + " received.");
   
   // 从文件系统中读取请求的文件内容
   fs.readFile(pathname.substr(1), function (err, data) {
      if (err) {
         console.log(err);
         // HTTP 状态码: 404 : NOT FOUND
         // Content Type: text/html
         response.writeHead(404, {'Content-Type': 'text/html'});
      }else{             
         // HTTP 状态码: 200 : OK
         // Content Type: text/html
         response.writeHead(200, {'Content-Type': 'text/html'});    
         
         // 响应文件内容
         response.write(data.toString());        
      }
      //  发送响应数据
      response.end();
   });   
}).listen(8080);
 
// 控制台会输出以下信息
console.log('Server running at http://127.0.0.1:8080/');
```
您在接下来将打开一个8080端口
[http://127.0.0.1:8080/](http://127.0.0.1:8080/)
您可以访问此网站，这是您的本地HTTP服务器。

接下来提供有关Node.js更多信息，您可以跳过。

[下载Node.js](https://nodejs.org/zh-cn/download/)
[文档](https://nodejs.org/zh-cn/docs/)
[关于](https://nodejs.org/zh-cn/about/)
[下载链接](https://nodejs.org/dist/v12.18.3/node-v12.18.3-x64.msi)
[百度Node.js](https://www.baidu.com/s?ie=utf-8&f=8&rsv_bp=1&tn=02003390_42_hao_pg&wd=Node.js&oq=node.js&rsv_pq=fbca7d9600004041&rsv_t=a3cb//WsKoa5vf1Nc0365JM6DCJb6c1RuqCq0MoAwejTSs3Nwf7n795gJxEIkWN6yfNsRxwW2pIE&rqlang=cn&rsv_enter=1&rsv_dl=tb&rsv_btype=t&inputT=967&rsv_sug3=5&rsv_sug1=4&rsv_sug7=100&rsv_sug2=0&rsv_sug4=1365&rsv_sug=2)
[node中文网](https://www.baidu.com/link?url=5IrbbnEnh3nK8C4OnEzMrMCkYbi3iegxf4Rqrwqfvx3&wd=&eqid=9192bdd8000039a1000000065f33ab9a)