[axios]: axios-js.com/docs/index.html

#### 1.HTTP请求交互基本过程

1. ######   客户端   请求

   - 请求行
   - 请求头
   - 请求体

2. ###### 服务器  请求

   - 状态行
   - 响应头
   - 实体内容

#### 2.HTTP请求报文

1. ###### 请求行:

   - java-大数据- 前端 -python 人工智能 百度 

   **method url**

   **GET/poduct_detail?id=2**

   **POST/login**

2. 多个请求头

   Host:www.baidu.com

   **Cokie**:BAIUID=AD3BFA706E;BIDUPSID=AD38OFA706;

   **Content-Type:**application/x-www-form-urllencoded 或者 application/json

3. 请求体

   - username=Tom&pwd=123 
   - {"username":"tom","pwd":123}

#### 3.HTTP响应报文

1. 响应状态行： **status statusText**
2. 多个响应头
   - Content-Type:text/html;charset=utf-8
   - Set-Cookie: BD_CK_SAM=1;path=/
3. 响应体
   -  html 文本、json 文本 js css img

#### 3.1 Post请求体格式

1. Content-Type:application/x-www-form-urlengcoded;charset=utf-8
2. 用于键值绝对参数，参数的键值用=连接，参数之间用&连接
3. 列如: name=%E5%B0%F%E6^98%8E&age=12\
4. Content-Type:application/json;charset=utf-8
5. 用于json 列如:{"name":"%E5%B0%E6%98%8E“,"age":12}
6. Content-Type:multpart/form-data

#### 4.常见状态码

**200   ok    请求成功 一般请求GET POST**

**201  Created 已创建 成功请求了新资源**

**401  Unauthorized  未授权/请求用户身份认证**

**404 Not Found  服务器 无法根据用户寻找资源**

**500 InternaI Server Error 服务器内请求错误 ，无法完成请求**



#### 5.不同类型请求作用

1. **GET 从服务器端读取数据**
2. **POST 向服务器端添加请求数据**
3. **PUT更新服务器端已请求数据**
4. **DELETE 删除服务器端数据**

#### 6.API分类

1. **REST API:  reastful**
   -   发送请求进行 **CRUD** 那个操作请求方式来决定
   - 同一个请求路径可以多个请求
   - 请求方式会用到 **GET/POST/PUT/DELETE**
2. **非 REST API: restlets**
   - 请求方式不决定请求的 **CRUD**操作
   - 一个请求路径只对应一个操作
   - 一般只有 **GET/POST**

#### AXIOS

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
<div>
    <button onclick="testGet()">GIT请求</button>
    <button onclick="testPost()">POST请求</button>
    <button onclick="testPut()">PUT请求</button>
    <button onclick="testDelete()">DELETE请求</button>
</div>
<script src="https://cdn.bootcdn.net/ajax/libs/axios/0.21.0/axios.min.js"></script>
<script>
    function testGet(){
        axios.get('http://localhost:3000/posts?id=1')
            .then(response=>{     git请求不需要携带参数提
            console.log('/posts get',response.data)
        })
    }

    function testPost(){
        axios.post('http://localhost:3000/posts',{"title":"json-server3","author":"typicode3"})
            .then(response=>{   post请求携带参数体
            console.log('/posts post',response.data)
        })
    }

    function testPut(){
        axios.put('http://localhost:3000/posts/3',{"title":"json-server...","author":"typicode..."})
            .then(response=>{
                console.log('/posts post',response.data)
            })
    }

    function testDelete(){
        axios.delete('http://localhost:3000/posts/3')
            .then(response=>{
                console.log('/posts post',response.data)
            })
    }

</script>
</body>
</html>
```

###### db.json

```json
{
  "posts": [
    {
      "id": 1,
      "title": "json-server",
      "author": "typicode"
    },
    {
      "id": 2,
      "title": "json-server2",
      "author": "typicode2"
    }
  ],
  "comments": [
    {
      "id": 1,
      "body": "some comment",
      "postId": 1
    }
  ],
  "profile": {
    "name": "typicode"
  }
}
```

###### package.json

```json
{
  "dependencies": {
    "cors": "^2.8.5",
    "express": "^4.17.1"
  }
}

```

- ​    https://github.com/typicode/json-server    git
- ​    在本地创建一个新的文件夹  下载 所需要的的  **cors,express**  两个依赖在本地
- ​    https://www.bootcdn.cn/  axios   打开所搜 axios 复制到  html / script src=" "

### 第二章 :  XHR 理解使用

###### MDN文档

http://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest