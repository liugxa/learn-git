## Web开发中利器：webpack

#### 目录
- 使用webpack命令将模块打包 (设置output的publicPath属性)
- 构建web service服务 (https://github.com/typicode/json-server)
- 配置webpack-dev-server(设置proxy server中的byPass方法)
- web测试(生成source map文件与javascript debug)

---

### 使用webpack命令将模块打包
有时又我们需要将output的publicPath属性设置成我们web应用的名称

```
var config = {
    context: __dirname,
    devtool: 'source-map',
    output: {
        path: __dirname + '/build/',
        filename: '[name]/[name].[hash].js',
        publicPath: '/platform/'
    },
    ..... .....
}
```

#### 配置webpack-dev-server
```
module.exports = {
	context: __dirname,
	devServer: {
		proxy: {
			'/platform/*' : {
				target: 'http://9.111.251.122:3004',
				bypass: function(req, res, proxyOptions) {
					if(req.url.indexOf("/ws") == -1){
						var r = req.url.substring(req.url.indexOf("/platform") + 9);
						return r;
					}
				}
			}
		}
	}
}
```

关于bypass方法的解释
http://webpack.github.io/docs/webpack-dev-server.html#bypass-the-proxy

Bypass the Proxy

(Added in v1.13.0) The proxy can be optionally bypassed based on the return from a function. The function can inspect the HTTP request, response, and any given proxy options. It must return either false or a URL path that will be served instead of continuing to proxy the request.

For example, the configuration below will not proxy HTTP requests that originate from a browser. This is similar to the historyApiFallback option: browser requests will receive the HTML file as normal but API requests will be proxied to the backend server.


```
proxy: {
  '/some/path': {
    target: 'https://other-server.example.com',
    secure: false,
    bypass: function(req, res, proxyOptions) {
      if (req.headers.accept.indexOf('html') !== -1) {
        console.log('Skipping proxy for browser request.');
        return '/index.html';
    }
  }
}
```

使用byPass方法，我们可以仅仅将应用中对于web service的访问请求发送到proxy上，而对于其他的文件请求，并不发送到proxy server上。

#### source-map文件与javascript debug
Javascript source map详解
http://www.ruanyifeng.com/blog/2013/01/javascript_source_map.html

