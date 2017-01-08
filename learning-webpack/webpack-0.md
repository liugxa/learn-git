## Web������������webpack

#### Ŀ¼
- ʹ��webpack���ģ���� (����output��publicPath����)
- ����web service���� (https://github.com/typicode/json-server)
- ����webpack-dev-server(����proxy server�е�byPass����)
- web����(����source map�ļ���javascript debug)

---

### ʹ��webpack���ģ����
��ʱ��������Ҫ��output��publicPath�������ó�����webӦ�õ�����

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

#### ����webpack-dev-server
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

����bypass�����Ľ���
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

ʹ��byPass���������ǿ��Խ�����Ӧ���ж���web service�ķ��������͵�proxy�ϣ��������������ļ����󣬲������͵�proxy server�ϡ�

#### source-map�ļ���javascript debug
Javascript source map���
http://www.ruanyifeng.com/blog/2013/01/javascript_source_map.html

