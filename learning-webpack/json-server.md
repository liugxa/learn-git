# json-server 构建web service服务

### 简介
json-server将Json与web server的概念巧妙结合在一起构建可用的web service服务。

以前构建一套可测试的web service，我们不得不依赖服务器端的技术实现，例如Apache CXF (http://cxf.apache.org)来完成，并且还要搭建web容器，从而让web service能够运行起来，在这些繁琐的步骤完成后，我们才能将注意力放在实际的开发任务上。

然而，随着NodeJs的出现，大量的框架与工具采用javascript来实现。其中Json-server的出现极大的简化了构建web service的工作。它将Json文件格式与web service巧妙的结合在一起，构建web service服务我们只需要编写如下的json文件


### 构建web service
```
{
  "posts": [
    { "id": 1, "title": "json-server", "author": "typicode" }
  ],
  "comments": [
    { "id": 1, "body": "some comment", "postId": 1 }
  ],
  "profile": { "name": "typicode" }
}
```

现在启动json server

```
$ json-server --watch db.json
```

如果需要修改server的服务端口，可以这样

```
$ json-server --watch db.json --port 3004
```

而且，我们和可以将json-server当作静态文件服务器，只需要建立
./public文件夹或者使用--static来设置文件夹的位置

```
mkdir public
echo 'hello world' > public/index.html
json-server db.json

json-server db.json --static ./some-other-dir
```

### Json-server的其他用法
参考
https://github.com/typicode/json-server