### vue

#### 1. 基本语法 指令  

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <div id="app"> 声明 el :"#app"名         1.
        {{nickname}}  采用 {{}} 来包裹渲染的  在data中定义   I
        <ul>
            <li v-for="(item,i) in list">  在父级 循环 v-for="里面都是js语法"  5.
                {{i}}.{{item}}    渲染到页面  6.  III 渲染列表采用 v-for="(item,i) in list"
            </li>
        </ul>
    </div>
   <script src="../vue/vue.js"></script>
    <script>
     let vm = new Vue({   (声明创建一个实例化)暂时用不到  new Vue就可以  
         el:"#app",  el 声明的 #名            2.
         data: function(){  定义data数据 并且返回数据    3.       
            return {
                nickname:"vue-渲染",   在data中定义 名字内容 II
                list:['AA','BB','CC'],   定义一个数组  4. 在上面渲染在DOM  
            }
         }
     })
    </script>

</body>
</html>
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <div id="app">
        {{nickname}}
        <fieldset>
            <legend>添加</legend>  1.   添加
            <div>图片 <input type="text" v-model="img"></div> 3.  v-model="img"  双向数据绑定  img
            <div>昵称 <input type="text" v-model="nickname"></div>
            <button @click="add">添加</button>  2. @click="add"  @clcik添加事件
        </fieldset>
        <ul>
            <li v-for="(item,i) in arr">
                <img v-bind:src="item.img" alt="" :style="{width:'300px' }"> :   :style="" 变成 js        9.
                <a v-bind:href="'detail.html?name'+item.name">{{item.name}}</a>  v-bind简写 :  绑定渲染元素  
                <button v-on:click="del(i)">删除</button> 8. v-on:click="删除"  v-on 点击事件 
            </li>
        </ul>
        <ul>
            <li v-for="(item,i) in list">
                {{i}}.{{item}}
            </li>
        </ul>   
    </div>
   <script src="../vue/vue.js"></script>
    <script>
     let vm = new Vue({
         el:"#app",
         data: function(){
            return {            4.           在定义 img  name  定义内容名字
                img:"https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=4254802126,1999767709&fm=26&gp=0.jpg",
                nickname:"伊丽莎白·奥尔森",
                nickname:"vue-渲染",
            list:['AA','BB','CC'],
            arr:[
                {
                  img:"https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=260792715,1806784404&fm=26&gp=0.jpg"
                    ,name:"奥黛丽.赫本"
                },
                {
                  img:"https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=2797902673,3909178716&fm=26&gp=0.jpg"
                    ,name:"丽芙·泰勒"
                } ,
                {
                  img:"https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=3007165768,826227765&fm=26&gp=0.jpg"
                    ,name:"斯嘉丽·约翰逊"
                },
                 {
                     img:"https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=3518973337,3493184901&fm=26&gp=0.jpg"
                    ,name:"凯特·贝金赛尔"
                }
            ]
            }
         },
         methods:{                                 定义方法的
             del(i){//删除                    添加   i 传参   7.
                //  alert(i)
                this.arr.splice(i,1)//截取数组   截取 数组里面的 i ,1 每一项的第一个
             },
             add(i){ 添加方法     
                alert('1111')
                this.arr.unshift({     this 添加到 数组里面头添加       5.
                    img:this.img,         图片到img 
                    name:this.nickname     名字  name    
                })
             }
         }
     })
    </script>

</body>
</html>
```

#### vue生命周期

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <div id="app">
        {{nickname}}
        <fieldset>
            <legend>添加</legend>
            <div>图片 <input type="text" v-model="img"></div>   
            <div>昵称 <input type="text" v-model="nickname"></div>
            <button @click="add">添加</button>
        </fieldset>
        <ul>
            <li v-for="(item,i) in arr">
                <img v-bind:src="item.img" alt="" :style="{width: w }">
                <a v-bind:href="'detail.html?name'+item.name">{{item.name}}</a>
                <button v-on:click="del(i)">删除</button>
            </li>
        </ul>
        <ul>
            <li v-for="(item,i) in list">
                {{i}}.{{item}}
            </li>
        </ul>   
    </div>
   <script src="../vue/vue.js"></script>
    <script>
        // Vue.config.devtools = false,
        // Vue.config.Vue.config.productionTip = false;
        let vm = new Vue({
            // template:"<h1>111111</h1>",    //  2.              如果你先传入 template 就先执行 template
            el:"#app",         //      3.  在执行 el:"#app"     el 
            beforeCreate() {//  创建前             ajax请求
                console.log('beforCreate',this.$data,this.$el)
            },
            created() {//后   数据追备好后            4.
                console.log('create',this.$data,this.$el)
            },
            beforeMount() {//更新前  
              console.log('beforeMount',this.$data,this.innerHTML)  
            },
            mounted() {//后  数据更新完成 5.   echarts   map   swiper  方法都放在 beformount
                console.log('mounted',this.$data,this.innerHTML)
            },
            beforeUpdate() {//挂载前
                console.log('beforeUpdate')
            },
            updated() {//后
                console.log('updated')
            },
            beforeDestroy() {//销毁前
                console.log('beforeDestroy')
            },
            destroyed() {//后
                console.log('destroyed')
            },

         data: function(){
            return {
                w:"100px",                
                img:"https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=4254802126,1999767709&fm=26&gp=0.jpg",
                nickname:"伊丽莎白·奥尔森",
                nickname:"vue-渲染",
            list:['AA','BB','CC'],
            arr:[
                {
                  img:"https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=260792715,1806784404&fm=26&gp=0.jpg"
                    ,name:"奥黛丽.赫本"
                },
                {
                  img:"https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=2797902673,3909178716&fm=26&gp=0.jpg"
                    ,name:"丽芙·泰勒"
                } ,
                {
                  img:"https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=3007165768,826227765&fm=26&gp=0.jpg"
                    ,name:"斯嘉丽·约翰逊"
                },
                 
                 {
                     img:"https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=3518973337,3493184901&fm=26&gp=0.jpg"
                    ,name:"凯特·贝金赛尔"
                }
            ]
            }
         },
         methods:{
             del(i){//删除
                //  alert(i)
                this.arr.splice(i,1)//截取数组
             },
             add(i){
                    this.arr.unshift({
                    img:this.img,
                    name:this.nickname
                })
             }
         }
     })
   

        // setTimeout(()=>{      //   1.            一般情况下不会用的    直接  el template  
        //     vm.$mount('#app')//传入#app 不用 el templte 也可以
        // },2000)

        // setTimeout(()=>{
        //     vm.$destroy()  //监听他在 4秒侯销毁调用
        // },6000)
    </script>

</body>
</html>
```

#### vue 轮播图

```vue
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .demo{
            margin: 0;
            padding: 0;
        }

        .demo li{
            width: 500px;
            height: 400px;
            list-style: none;
        }
    </style>
</head>
<body>
   <div id="app">
    <ul class="demo">
        <li v-show="i === activeIndex" v-for="(item,i) in listimg" >
            <img :src="item.img" alt="" :style="{width: w ,height:'calc(100vh * 0.6)'}">
        </li>
    </ul>
   </div>
    <script src="../vue/vue.js"></script>
    <script>
        let vm = new Vue({
            el:"#app",           
            data(){
                return{
                    activeIndex:0,
                    w:"calc(100vw * 0.3)",
                    listimg:[
                        {
                            img:"https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=515472328,331573341&fm=26&gp=0.jpg"
                        }   ,
                        {
                         img:"https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=2246284282,3299805659&fm=26&gp=0.jpg"
                        },
                       {
                           img:"https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=3768851216,4067832036&fm=26&gp=0.jpg"
                       },
                        {
                            img:"https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=1136384998,901029167&fm=26&gp=0.jpg"
                        },
                        {
                            img:"https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=1911379816,1115164849&fm=26&gp=0.jpg"
                        }
                    ]
                }
            },
            mounted(){
                setInterval(()=>{
                    this.activeIndex++
                    if(this.activeIndex === this.listimg.length){
                        this.activeIndex = 0
                    }
                },1000)
            }
        })


    </script>
</body>
</html>
```

#### 回顾生命周期

1. 初始化
2. 执行 beforeCreate 钩子函数 (如果有)
3. 初始化data数据
4. 判断是否传入 el:" ",(如果有)
5. 如果没有传入，则等到实例vm主动调用$mount()在继续执行
6. 如果传入el,在判断是否有传template模板选项
7. 如果没有传入template,则将el对容器内的所有内容当成，template
8. template通过render函数编译成vdom成DOM

```html
<div id="app">
    <input v-model='nickname'/>
</div>

let domtree = {
domProps:{
    id:'app',
     name:"myname",
    'class':"container",
	slots:[
		{
			tag:"input",
				domProps:{
value:nickname
},
onClcik(e){
this.value = e.target.value
}
}
]
}
}
```

10. 执行beforMount钩子函数 (如果有)
11. 将虚拟DOM替换el容器中旧内容 (HTML覆盖旧的模板)
12. 执行 mounted钩子函数 (如果有)
13. data数据发生改变，先走beforeUpdate, VDOM更细完成 DOM 后，走updated
14. 当组件切换或者挑战路由销毁VUE实例时，调用beforDestroy钩子函数 (如果有)
15. 接触事件绑定销毁组件
16. 执行destroyed钩子函数 (如果有)