# Vue阶段综合演练

[TOC]

# 一、项目概要

## 1、效果前瞻

仿照网站：卖座网

![效果预览](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/10/cbf14ac0b60d10ba7cac70cd93f87af85d26a06b.png?sign=3d94c060b86cc17a523f2f153bfc4485&t=5f7c13a9)



## 2、开发流程

- 产品**立项** (需求分析、技术选型、项目人员确定)
  - 项目立项报告（百度搜）【产品经理，PM】
    - 当前背景
    - 项目需求
    - 人员安排
    - 功能介绍
    - 市场需求
    - 项目风险
- 产品原型 (设计产品原型图— 进行ui设计)
  - 产品原型图
- 项目开发 (前端 与 后端)【周期最长的一步】
  - 设计（UI）：设计图和切图
  - 前端：出一版静态页（模板）
  - 后端：服务器端
- 项目测试
  - 测试部门：QA
- 项目上线
  - 运维&后端



## 3、开发环境

- 开发工具：vs code并安装vue开发插件：Vetur

- 开发环境：windows /mac

- 项目运行环境：node v10+

- Vue脚手架： vue-cli 4.5.7

- 代码版本工具：Git/Gitee



# 二、初始化及必要知识点

## 1、初始化远程仓库

> 以Github为例：https://github.com/

- 创建一个新项目

![创建项目](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/10/306929e959182a95bde37358ccab47ce0842b100.png?sign=1a495fc0bde2637359bee1e4d0c92f50&t=5f7d46b9)



- 仓库配置

![仓库配置](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/10/f4d0bdf4868f9e4391a08e500c3b41fa265bde96.png?sign=d4e36722cdba0f62c2ec2c0c352b57a5&t=5f7d4765)





## 2、创建项目

- 使用`vue-cli`脚手架创建项目

~~~shell
vue create jy-moive
~~~

> 项目名称`jy-moive`可以根据自己的情况进行替换



- 脚手架创建项目询问式选择回答如下

![q1](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/10/250eb3908e6d6f1e7030de93a4cc4b7d0ea23d80.png?sign=a8bb298760970b88d096ccd1ab327325&t=5f7d4898)

![q2](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/10/6d71cfd2736ef70031ecba9b00d5547f8c8a929e.png?sign=937ca6106ff402d047520b5383e30ffa&t=5f7d493d)

![q3](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/10/09310bc207273240ec618ed3b5e08446a7825f21.png?sign=712e7c92f558ab676e463c8f4716061a&t=5f7d4976)

![q4](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/10/f36dd956c10bd37a0b41e58bd307410a890be694.png?sign=0640aaf43e5bb7e8e29d11e386284bfc&t=5f7d49c0)

![q5](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/10/62cd3398cd8e4e350f829c5e0004ad1488ccef9e.png?sign=339953ee56cd30cf22dae3ad2beec50d&t=5f7d4a0d)

![q6](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/10/61382bbc0f20ce8c9298aecb16e236bb854e5a8e.png?sign=18f3f9060736bfe48c710a3f7ae91b01&t=5f7d4a31)

![q7](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/10/37730d5e7e2fcdd38034a888abbf8397db681c1b.png?sign=f4e8c82a663746e20f703770bbf2f982&t=5f7d4a5b)



- 项目创建完毕

![创建完毕](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/10/508f94e359c758bc9ca19ae83ac25cb361b499b8.png?sign=91a61753e74d1fd7195216d9c2bdc366&t=5f7f474d)



- 同步初始化项目到远程仓库

~~~shell
cd jy-moive
git remote add origin 远程仓库地址
git push -u origin master
~~~



- 创建开发分支`dev`

~~~shell
git branch dev
git checkout dev
git push -u origin dev
~~~



- （==可选操作==）为当前项目设置记住密码

> 如果每次提交都提示输入帐号密码，则可以做此步骤。
>
> 修改当前项目中的`.git/config`文件

将配置：

~~~config
[remote "origin"]
	url = https://github.com/......
~~~

修改为：

~~~config
[remote "origin"]
	url = https://用户名:密码@github.com/......
~~~



**后续每天工作使用Git指令是什么？？**

~~~shell
# 将远程仓库的代码拉取到本地
git pull

# 写代码的环节

# 写好代码
git add .
git commit -m "注释"

# 下班
git push
~~~



## 3、路由规划

如果项目中所有的路由都写在入口文件中，那么将不便于编写项目和后期维护。因此路由需要进行模块化处理。

可以**先行**添加以下几个空的路由模块：

- 电影模块
- 影院模块
- 个人中心模块

> 如果后续还有其他模块，届时再进行增加即可。

**创建各个模块对应的视图组件文件**

> - 在`src/views`目录下创建对应的文件夹与文件，同时，可以删除自带的`Home.vue`与`About.vue`文件
>
> - 创建每个视图组件后在其中书写好基本内容
>
>   - ~~~html
>     <template>
>         <div>
>             <h1>XXXX</h1>
>         </div>
>     </template>
>     ~~~

~~~text
src/views             
    ├─Center		（个人中心）         
    │      └─Center.vue 
    │                
    ├─Cinema 		（电影院）        
    │      └─Cinema.vue 
    │                
    └─Film          （电影）
           │ Film.vue
           │ NowPlaying.vue
           └─ComingSoon.vue
~~~

**创建模块化的目录及路由文件**

> 在每个路由模块文件中注册好对应的路由及各自所使用的视图组件

~~~text
src/router
    ├─index.js
    │
    └─routes
    	 │ center.js
         │ cinema.js
         └─film.js
~~~

**在剔除`router/index.js`中无用代码后，示例代码如下**

~~~javascript
import Vue from "vue";
import VueRouter from "vue-router";

// 导入路由模块
import centerRouter from '@/router/routes/center'
import cinemaRouter from "@/router/routes/cinema";
import filmRouter from "@/router/routes/film";

Vue.use(VueRouter);

const routes = [
    // 注册路由模块
    centerRouter,
    cinemaRouter,
    filmRouter,
    {
        path: "/",
        redirect: "/film",
    }
];

const router = new VueRouter({
    mode: "history",
    // 前缀暂时可以不用使用
    // base: process.env.BASE_URL,
    routes,
});

export default router;
~~~



## 4、底部导航

> 开始之前可以删除原先创建项目自带的`src/components/HelloWolrd.vue`文件

- 在`src/components/`目录下新建`FooterNav.vue`文件

![新建脚组件](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/10/fe909d0c1a9f44d8e075fded5de12addb75c3cfa.png?sign=8b8032361a9ad4d76af6b6b3e8c06f69&t=5f7f4ddd)

- 将需要的字体文件夹放置到`src/assets`目录下

> 字体文件夹在今日的`docs`目录下

![字体文件](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/10/eb7b29ea1e55e847f5d1f3c9f3aa079933e8e9ce.png?sign=640a8e620178ef8d7f323f25f3a3c473&t=5f7f0108)



- 将组件`src/components/FooterNav.vue`导入到根组件`App.vue`中并使用

> 同时需要清理根组件中无用的代码

~~~vue
<template>
    <div>
        <!-- 底部导航 -->
        <FooterNav></FooterNav>
        <!-- 路由容器 -->
        <router-view></router-view>
    </div>
</template>
<script>
import FooterNav from "@/components/FooterNav";

export default {
    components: {
        FooterNav,
    },
};
</script>

<style lang="scss">
* {
    margin: 0;
    padding: 0;
}
html,
body {
    touch-action: none;
    height: 100%;
    ul,
    li {
        list-style: none;
    }
}
</style>
~~~

> **注意：App.vue根组件中style标签不能加`scoped`！！**

- 编写组件`src/components/FooterNav.vue`代码，产生公共底部导航

~~~vue
<template>
    <div class="nav">
        <ul>
            <router-link to="/film" active-class="active" tag="li">
                <i class="iconfont icondianying"></i>
                <p>影片</p>
            </router-link>
            <router-link to="/cinema" active-class="active" tag="li">
                <i class="iconfont iconyingyuan"></i>
                <p>影院</p>
            </router-link>
            <!-- <router-link to="/" active-class="active" tag="li">
                <i class="iconfont iconzixun"></i>
                <p>资讯</p>
            </router-link> -->
            <router-link to="/center" active-class="active" tag="li">
                <i class="iconfont icongeren"></i>
                <p>个人</p>
            </router-link>
        </ul>
    </div>
</template>

<script>
// import导入样式
// import "@/assets/iconfont/iconfont.css";

export default {
    data() {
        return {};
    },
    mounted() {},
};
</script>

<style lang="scss" scoped>
.nav {
    position: fixed;
    bottom: 0;
    left: 0;
    border-top: 1px solid #ccc;
    height: 50px;
    text-align: center;
    background: #fff;
    color: #7a7e83;
    width: 100%;

    ul {
        display: flex;
        align-items: center;
        li {
            margin-top: 5px;
            flex: 1;
            height: 43px;
            &.active {
                color: #fe5100;
            }
            p {
                margin-top: 2px;
            }
            i {
                font-size: 20px;
            }
        }
    }
}
</style>
~~~

> 注意点：scss中的`&`写法  
>
> `&`表示它的父级，例如上述代码中，&.active可以理解成`li.active`。

> 注意点：关于router-link
>
> - tag属性：默认情况下，router-link生成的导航链接是`a`标签，如果需要生成指定的标签，可以添加tag属性，属性值就是需要生成的标签名字，例如生成li标签：tag="li"
> - active-class属性：给导航添加激活的样式，激活的样式名就是其属性值



- 整合好后应该得到如下效果

![效果](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/10/113ee549c18be1f14d0219dd2742f4eabad7e2ab.gif?sign=abf897af1e25ecc1dfae5340605d5901&t=5f7f1cbb)





## 5、网络请求

> 本次项目中使用axios进行网络请求，vue脚手架默认没有安装，需要自行安装才能使用。

- 安装axios

~~~shell
npm i -S axios
~~~



### 5.1、请求拦截器

**目的：**在请求`发出去之前`/`收到响应之后`做一些操作

**请求拦截器**

![请求拦截器](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/08/f470c12af2ae587dca702853839302f1a1466b04.png?sign=474304acf2f587da38ad40accd3bd77d&t=5f3d0b84)

**示例代码：**

~~~javascript
axios.interceptors.request.use(function(config){
    // 在请求发出去之前进行一些信息设置
    return config;
},function(err){
    // 处理响应的错误信息
    return Promise.reject(error);
});
~~~

**在`src/main.js`文件中体验**

~~~javascript
// 导入axios
import axios from "axios"
// 设置请求的基础域名
axios.defaults.baseURL = 'https://m.maizuo.com'

// 添加请求拦截器
axios.interceptors.request.use(function(config) {
    config.headers = {
        "X-Client-Info": '{"a":"3000","ch":"1002","v":"5.0.4","e":"1598087896889693885431809","bc":"110100"}',
        "X-Host": "mall.film-ticket.film.list",
    }
    // 在发送请求之前做些什么
    return config;
}, function(error) {
    // 对请求错误做些什么
    return Promise.reject(error);
});

axios.get("gateway?cityId=110100&pageNum=1&pageSize=10&type=1&k=8591124");
~~~

如果请求成功则会获取到类似以下信息：

![请求封装测试](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/10/f400ebfb8da0260d1547ea48a721a08eeb4d7db0.png?sign=62387ba3517efe7236779ff3130b7d3e&t=5f7f2a0a)

> 注意：
>
> 此处在`main.js`中写的这段代码仅用于
>
> - 请求拦截器知识点讲解
> - **卖座网数据数据请求注意点讲解**（需要2个特殊的请求头）
>
> 后面在实现功能时**不在**此处写请求代码！！！



## 6、ES6模块化语法（认识）

### 6.1、默认导出与默认导入

- 默认导出语法：`export default 默认导出的成员`

示例文件名假设为“m1.js”

~~~javascript
let a = 10
let c = 20
let d = 30
function show()
{
    
}
export default {
    a,
    c,
    show
}
~~~

- 默认导入语法`import 接收名称 from '模块标识符'`

~~~javascript
import m1 from './m1.js'
console.log(m1)
// 打印结果为
{a: 10,c: 20, show: [Function: show]}
~~~

> 注意点：每个模块中只允许使用唯一的一次`export default`，否则会报错。



### 6.2、按需导出与按需导入

- 按需导出语法`export let s1 = 10`

~~~javascript
// 当前文件模块为m1.js
// 分别按需导出s1、s2、say
export let s1 = 'aaa'
export let s2 = 'ccc'
export function say = function(){}
~~~

- 按需导入语法`import {s1 as aliasname} from '模块标识符'`

~~~javascript
// 导入模块成员
import {s1, s2 as ss2,say} from './m1.js'
console.log(s1)		//aaa
console.log(ss2)	//ccc
console.log(say)	//[Function: say]
~~~

> - 默认导入导出与按需导入导出可以共存，并不冲突。
> - 在一个模块中可以多次按需导出，但只能一次默认导出
> - 按需导出的成员在导入的时候可以通过`as`关键词起别名



### 6.3、直接导入并执行代码

有时候，我们只想单纯的执行某个模块中的代码，并不需要得到模块中向外暴露的成员，此时，可以直接导入并执行模块代码。

例如有以下代码：

~~~javascript
// 当前为m2.js模块
for(let i = 0;i < 3;i++){
    console.log(i)
}
~~~

~~~javascript
// 直接导入并执行模块代码
import './m2.js'
~~~



# 三、电影列表开发

## 1、列表顶部导航

- 创建电影列表顶部导航组件`src/components/FilmListTopNav.vue`

~~~vue
<template>
    <nav>
        <ul>
            <router-link tag="li" to="/film/nowplaying" active-class="active">
                <span>正在热映</span>
            </router-link>
            <router-link tag="li" to="/film/comingsoon" active-class="active">
                <span>即将上映</span>
            </router-link>
        </ul>
    </nav>
</template>

<style lang="scss" scoped>
nav {
    width: 100%;
    height: 50px;
    line-height: 50px;
    border-bottom: 1px solid #ccc;
    ul {
        display: flex;
        text-align: center;
        li {
            flex: 1;
            display: flex;
            justify-content: center;
            &.active {
                span {
                    width: 40%;
                    border-bottom: 2px solid red;
                    display: block;
                    color:#fe5100;
                }
            }
        }
    }
}
</style>
~~~

- 创建顶部导航对应的2个列表视图组件`src/views/Film/`目录下的`Nowplaying.vue`和`Comingsoon.vue`

![创建2个子视图组件](https://storage.lynnn.cn/assets/markdown/91147/pictures/2020/10/3887dd7be6758078936e0a4b992698757511df23.png?sign=7b6136858095bb48d815a94aac617f6b&t=5f7f3a14)

- 在电影路由模块文件中定义上一步两个视图组件对应的路由（子路由）

~~~javascript
// 电影路由
export default {
    // 页面请求uri
    path: '/film',
    component: () => import('@/views/Film/Film'),
    // 子路由 嵌套路由
    children: [{
            // /film/nowplaying
            path: 'nowplaying',
            component: () => import('@/views/Film/NowPlaying')
        },
        {
            path: 'comingsoon',
            component: () => import('@/views/Film/ComingSoon')
        },
        {
            path: '/film',
            redirect: 'nowplaying'
        }
    ]
}
~~~

- 在电影视图组件`src/views/Film/Film.vue`中导入顶部导航组件

~~~vue
<template>
    <div>
        <FilmListTopNav></FilmListTopNav>
        <router-view></router-view>
    </div>
</template>

<script>
import FilmListTopNav from '@/components/FilmListTopNav'
export default {
    components: {
        FilmListTopNav
    }
}
</script>
~~~



## 2、请求封装

**原因：**我们的项目前期数据都来自于卖座网，每个组件中的数据都要进行网络请求获得，但是每个网络请求的参数存在差异，为了避免因参数差异而重复去书写网络请求的代码，此处我们可以对请求进行封装。目的是，当传递了不同的参数就去请求对应的数据。

**实现步骤：**

- 创建`src/config/url.js`文件
  - 作用：配置各个页面需要数据请求的地址
- 创建`src/api/http.js`文件
  - 封装`axios`网络请求
- 创建`src/api/api.js`文件
  - 调用封装的`axios`进行具体的数据请求

**实际操作：**

- 创建`src/config/url.js`文件

~~~javascript
// 电影列表 pageNum=数字
export const nowPlayingListUri =
    "/gateway?cityId=110100&pageSize=30&type=1&k=5155219&pageNum=";
// 即将上映
export const comingSoonListUri =
    "/gateway?cityId=110100&pageSize=30&type=2&k=5155219&pageNum=";

// 后续需要可以再添加...
~~~

- 创建`src/api/http.js`文件

~~~javascript
import Vue from "vue";
import axios from "axios";
axios.defaults.baseURL = "https://m.maizuo.com";
// 添加请求拦截器
axios.interceptors.request.use(
    function(config) {
        let host = "";
        let info = config.headers.info;
        if ("info" == info) {
            // 详情页面的头
            host = "mall.film-ticket.film.info";
        } else if ("cinema" == info) {
            // 影院列表
            host = "mall.film-ticket.cinema.list";
        } else if ("city" == info) {
            host = "mall.film-ticket.city.list";
        } else {
            // 列表信息的头
            host = "mall.film-ticket.film.list";
        }
        config.headers = {
            "X-Client-Info":   '{"a":"3000","ch":"1002","v":"5.0.4","e":"1598087896889693885431809","bc":"110100"}',
            "X-Host": host,
        };
        return config;
    },
    function(error) {
        // 对请求错误做些什么
        return Promise.reject(error);
    }
);

export default axios;
~~~

- 创建`src/api/api.js`文件

~~~javascript
// 引入封装头信息和请求域名的axios对象
import http from './http'
// 引入请求的url地址
import {
  // 正在热映列表请求uri地址
  nowPlayingListUri,
  comingSoonListUri,
} from '@/config/url'

/**
 * 获取正在热映列表分页数据
 * @param {int} page 页码数 默认1 
 * @returns promise对象
 */
export const nowPlayingListData = (page = 1) => {
  return http.get(nowPlayingListUri + page)
}
~~~



## 3、列表功能

### 3.1、正在热映

> 修改`src/views/Film/NowPlaying.vue`文件







### 3.2、即将上映









