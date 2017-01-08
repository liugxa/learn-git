# json-server ����web service����

### ���
json-server��Json��web server�ĸ�����������һ�𹹽����õ�web service����

��ǰ����һ�׿ɲ��Ե�web service�����ǲ��ò������������˵ļ���ʵ�֣�����Apache CXF (http://cxf.apache.org)����ɣ����һ�Ҫ�web�������Ӷ���web service�ܹ���������������Щ�����Ĳ�����ɺ����ǲ��ܽ�ע��������ʵ�ʵĿ��������ϡ�

Ȼ��������NodeJs�ĳ��֣������Ŀ���빤�߲���javascript��ʵ�֡�����Json-server�ĳ��ּ���ļ��˹���web service�Ĺ���������Json�ļ���ʽ��web service����Ľ����һ�𣬹���web service��������ֻ��Ҫ��д���µ�json�ļ�


### ����web service
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

��������json server

```
$ json-server --watch db.json
```

�����Ҫ�޸�server�ķ���˿ڣ���������

```
$ json-server --watch db.json --port 3004
```

���ң����ǺͿ��Խ�json-server������̬�ļ���������ֻ��Ҫ����
./public�ļ��л���ʹ��--static�������ļ��е�λ��

```
mkdir public
echo 'hello world' > public/index.html
json-server db.json

json-server db.json --static ./some-other-dir
```

### Json-server�������÷�
�ο�
https://github.com/typicode/json-server