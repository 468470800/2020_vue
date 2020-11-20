- #### day01笔记
  
  ##### 1，四阶段前导
  
  ------
  
  1. ###### 前端内容        
  
     - html/css / html5  css3
     - 项目 (移动端 ， PC)        
     - 目标 :  熟练掌握静态页面 (语义化， 结构化， 清晰化)
     - 实现 (HTML语义化清晰化) 多看 ， 多写， 
  
  2. ###### JavaScript 
  
     - **javascript  / jquery  / touch /ajaxjs 高效**
     - 完成交互
     - 提高交互自己如何思考
     - NODE
     - 框架
     - 小程序
     - 技术指导 
       - NODE
       - node模块 http/fs/url/path... express, koa, mysql, es6, webpack
       - 目标: 对于前后端有个完整的认知;   增进es6语法知识， 掌握webpack 使用。
  
  3. ######    框架    
  
     - **框架  Vue     React **
  
       - 时间  19T  13Tvue(5T), 6T React  (1T)
       - 需要掌握实际工作中运用技术内容
       - ***量达到质变！！！！***(vue项目做两遍)， 语法内容 至少5遍	       
       - 能力要求:  
         - 	***阅读文档能力！！!***          
         - 	**解决问题能力  !   (问题点， 如何解决)**               
         - 	**实战能力！！！！！！！**
  
     - 小程序  
  
       - 	小程序     数据可视化
  
       技术指导
  
       -    串讲， 回顾， 项目！！！！
  
  #### 2,  vue介绍
  
  ------
  
  ##### 2.    1，什么是 vue框架
  
  - 文档地址  ：   https://cn.vuejs.org/
  
  - 作者 :  尤雨溪
  
- 含义: **Vue 是一套用于构建用户界面的渐进式框架。**与其它框架不同,Vue是被设计师认可自底向上应用。**Vue的核心库只关注视图层。**不仅容易上手，还便于第三方库或文件 项目整合。另一方面，当与现代化工具支持相结合使用时，Vue 也完全能够为复杂单页面应用提供驱动。           但是Vue.js解决了这些问题，这些问题都在Vue中小时
  
    #### 2.2，为什么使用vue
  
    - 我们知道完整网页是由DOM元素组成视图结构，再加上CSS样式修饰，结合javascript实现用户进行交互。我们把基本的试图开发层，这部分就是Vue核心关注的部分，为神魔关注他呢?因为一些页面元素非常多，结构之间还存在依赖或者依存关系，代码上就会出现很多问题。
  
      用过 **JQuery**的开发人员都有这样的体会，在页面元素不多的时候，有时候需要一层层向上寻找父辈元素，随着项目规模不断扩大，页面结构和代码会变得越来越臃肿，而JQuery选择器DOM操作本身也存在性能缺失问题，原本轻巧简介JQuery代码变得无从下手增加 维护成本。
  
      但是Vue.js解决问题，这些问题都将在Vue中消失。
  
      #### 2.3 特点   
  
      - **轻量级框架**
      - **双向绑定**
      - **指令**
      - **客户端路由**
      - **状态管理**	
  
  #### 3，基础使用
  
  ------
  
  - 开发环境  
  
    - 生产环境:   开发结束， 部署
  
      ```js
      <!-- 开发环境版本，包含了有帮助的命令行警告 -->
      <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
      ```
  
      
  
    - 开发环境:  开发中
  
      ```html
      <!-- 生产环境版本，优化了尺寸和速度 -->
      <script src="https://cdn.jsdelivr.net/npm/vue"></script>
      
      ```
  
      #### 3.2,  基础使用
  
      - 安装  
  
      - 挂载
  
      - 实例vue对象
  
      - ```html
        <!DOCTYPE html>
        <html lang="en">
        <head>
            <meta charset="UTF-8">
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            <meta http-equiv="X-UA-Compatible" content="ie=edge">
            <title>Document</title>
            <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
        </head>
        <body >
            <!-- 写一个标签容器 -->  
            <div id="app">
                <h1>{{msg}}</h1>
                <p>{{chbds}}</p>
                <h5>{{htmlstr}}</h5>
            </div>
           
                <h1>{{msg}}</h1>
                <p>{{chbds}}</p>
                <h5>{{htmlstr}}</h5>
            <script>
                
            let vm = new Vue({//第三步  实例化一个Vue对象
                el:"#app",
                data:{
                    msg:"常山",
                    chbds:"data 里面的数据我们可以通过模板中通过插值表达式进行展示",
                    htmlstr:'<b>8866</b>'
                }
            });
        
            setInterval(() => {
                vm.msg += "我来了"
            }, 1000)
        	
        	//当页面data里面 的数据发生改变视图 也会跟着改变双向数据 绑定
        
                console.log(vm);
                console.log(vm.msg);
                console.log(vm.htmlstr);
        
            //挂载节点 将这个vue实例作用节点范围关联起来 
            //data  数据对象  节点范围使用到的数据
            //data 里面的数据我们可以通过模板中通过插值表达式进行展示！{{data中变量}}
            //data 里面的变量数据，最后变成了这个vue实例 属性
        	//data 里面的变量数据一旦发生改变页面数据会自动更新 ！
        
            //vue.js:634 [Vue warn]: Do not mount Vue to <html> or <body> - mount to normal elements instead.
            // 写在body 上了
        
            //vue基础使用.html:18 Uncaught ReferenceError: Vue is not defined
            //没有引入vue  
        
            ///{{msg}}  写在标签外面访问不到
            </script>
        </body>
        </html>
        ```
  
      - 注意 点:
  
        - el  挂载  节点  将这个vue实例合作用节点范围关联起来 
  
        - data  数据对象  节点 范围 内可以使用到数据
  
        - data里面数据，我们可以在模板中通过插值表达式进行展示！
  
          ```
          {{data中变量}}
          ```
  
          
  
  
  
  #### 4，常见指令
  
  ------
  
  ##### 		4.1， 指令概念 
  
  - 指令的含义
  
    - 		指令就是**vue**给标签新增加的新属性，以**v-**开头
  
  - 使用
  
    ```html
    <标签 id="" class="" v-指令="变量/表达式"></标签>
    <标签 id="" class="" v-指令="'msg'+haha"></标签>指令和插值表达式一样
    v-bind:简写
    <标签 id="" ：class="" v-指令="'msg'+haha"></标签>
    ```
  
    
  
  #### 4.2 常用
  
  ------
  
  ```html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title></title>
  		<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
  	</head>
  	<body>
  		<div id="app">
  			<ul>
  				<li v-for="val in list">{{val}}</li>
  			</ul>
  			<hr>
  			<ul>
  				<li v-for="item in person">{{item}}</li>
  			</ul>
  			<ul>
  				<li v-for="(item,key,idx) in person">{{item}}{{key}}{{idx}}</li>
  			</ul>
  			<ul>
  				<li v-for="item in student">
  					<h3>姓名:{{item.name}}  <span>性别:{{item.sex ? '男':'女' }}</span> </h3>
  					<ul>
  						<li v-for="val in item.score">{{val.txt}} {{val.num}} </li>
  					</ul>
  				</li>
  			</ul>
  			<hr>
  			<div v-if="student.length">
  				<div v-for="item in student" class="item">
  					<h3>姓名:{{item.name}} <span>性别:  {{item.sex ? "男" : "女" }} </span> </h3>
  					<ul v-for="val in item.score">
  						<li >学科: {{val.txt}} ---- 分数 {{val.num}} </li>
  					</ul>
  				</div>
  				<p v-else>暂无数据</p>
  			</div>
  		</div>
  
  		<script type="text/javascript">
  			new Vue({
  				el: "#app",
  				data: {
  					list: [111, 22, 33, 444, 55555, 666666],
  					person: {
  						name: "谢文东",
  						age: 23,
  						sex: "男"
  					},
  					student: [{
  							name: "岳飞",
  							sex: 1,
  							score: [{
  								txt: "语文",
  								num: 100
  							}, {
  								txt: "数学",
  								num: 100
  							}]
  						},
  						{
  							name: "李靖",
  							sex: 1,
  							score: [{
  								txt: "语文",
  								num: 98
  							}, {
  								txt: "数学",
  								num: 96
  							}]
  						},
  						{
  							name: "李清照",
  							sex: 0,
  							score: [{
  								txt: "语文",
  								num: 100
  							}, {
  								txt: "数学",
  								num: 100
  							}]
  						}
  					]
  				}
  			});
  			<!-- <标签 v-for ="值   in 数组/对象"></标签> -->
  			<!-- <标签 v-for ="值,键   in 数组"></标签> -->
  			<!-- <标签 v-for ="值，键 下标 in 对象"></标签> -->
  			// v-if  和 v-for 一般不放在一起使用! 除非列表数据进行部分展示会一起使用
  		</script>
  	</body>
  </html>
  
  ```
  
  - v-if
  
    -   作用 : 条件内容渲染 (不满足条件节点不存在)
  
    - 使用: 
  
      ```html
      <标签 v-if ="表达式/变量"></标签>
      <标签 v-else-if ="表达式/变量"></标签>
      <标签 v-else></标签>
      ```
  
      **注意点: 必须紧邻！**
  
    - **v-show**
  
      - 作用: 条件渲染内容,(不满足， display:none)
  
      - 使用:
  
        ```html
        <标签 v-show ="表达式/变量"></标签>
        <标签 v-show ="!表达式/变量"></标签>
        ```
  
      - 注意点:
  
        - v-show 无论条件成立于否，节点都存在, 条件成立才会显示。
        - v-if条件成立节点才会显示存在，不成立不存在！
        - **什么时候使用v-show 和 v-if**
        -  需要反复展示内容的时候内容展示 v-show 指令，渲染一次使用  v-if
  
        ###### v-for
  
        - 作用: 渲染列表数据
  
        - 使用:
  
          ```html
          <标签 v-for ="值 in 数组/对象"></标签>
          <标签 v-for ="(值,键)in 数组/对象"></标签>
          <标签 v-for ="(值,键,下标)in 对象"></标签>
          ```
  
        - 注意点
  
          - 	**双层嵌套，注意标签标识符不重复，内存 循环是哪个内容**
  
            - **v-if  和 v-for 一般不在一起使用！**除非对列表的数据进行部分展示的时候，会在一起使用！
  
            - 当他们处于同一节点，v-if的优先级比 v-if 更高，这意味着 v-if 将重复运用每个v-for循环
  
            -  vue框架，采用的是虚拟DOM。
  
              当Vue正在更新使用 v-for 渲染的元素列表时它默认使用**就地复用**的策略。入股数据项的顺序被改变，Vue将不会赢DOM 元素匹配 数据的顺序就是就地跟新每个匀速，并且确保他们在每个元素正确的位置渲染， 这个类似Vue 1.x的tack-by = "$index"。
  
              这个默认的模式就是高效的，但是只**适合用于不依赖组件状态或临时DOM状态 表达输入值的列表渲染输出。**
  
              - **添加 key 属性(key唯一！)**
  
                ```html
                <!DOCTYPE html>
                <html>
                	<head>
                		<meta charset="utf-8">
                		<title></title>
                		<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
                	</head>
                	<body>
                		<div id="app">
                				<input type="text" key="1" v-if="num%2" placeholder="用户名">
                				<input type="text" key="2" v-else placeholder="邮箱">
                		</div>
                		<script type="text/javascript">
                			let vm = new Vue({
                				el:"#app",
                				data:{
                					num:1
                				}
                			});
                			
                			setInterval(()=>{
                				vm.num++;
                			},2000)
                			
                			// 就地复用！！！ 只改变部分 提高了渲染速度 减少DOM操作
                			// 有问题！ 某些情况不应该采用就地复用
                			// 解决问题 ; 给每个项目加上一个Key属性，且key值不猛形同要唯一！
                			
                		</script>
                	</body>
                </html>
                
                ```
  
              - **v-once**
  
                - 作用 : 一次性绑定！数据变化了，页面就不会更新！
  
                - 使用
  
                  ```html
                  <标签 v-once ="变量"></标签>
                  <标签 v-once v-html="变量"></标签>
                  <标签 v-once v-bind:class="变量"></标签>
                  ```
  
                - **v-on**
  
                - **v-model**
  
  ### 5，事件绑定
  
  
  
  
  
  ------
  
- ​      注意:加密以这块我们根据后台的要求,只加密了openid uid 以及salt等属性以及属性值,用的是md5
  