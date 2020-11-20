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

