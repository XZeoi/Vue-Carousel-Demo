# Vue-Carousel-Demo

利用Vue制作轮播图的Demo，所使用栈有`**HTML**`、`**CSS**`、`**Vue**`、`**axios**`等；  
因为数据很少，所以直接用JSON文件模拟；

## 待实现功能
  1、网页刷新时，轮播图照片按一定时间间隔显示，并循环重复显示；  
  2、随着照片的轮播，指示小点indicator依次跳动；  
  3、鼠标移进去时，轮播停止；  
  4、鼠标移出来时，轮播继续；  
  5、点击左按钮，跳到上一张照片；点击右侧按钮，跳到下张照片

## 制作思路
  1、先把所有的照片都放在视图中，并给所有照片一个标记；  
  2、创建一个中间变量，随着时间改变这个中间变量；  
  3、当照片标记与中间变量相等时，展示该照片；
  
## 关键点讲解
  1、因为Demo很小，并没有用`webpack`或者`vue-cli`来搭建项目。除了CSS样式外，本demo直接在index.html中建立。所以直接利用下载的`vue.min.js`和`axios.min.js`库。  
  2、整个程序的重点思路：      
    - 数据的加载在Vue生命周期中`mounted`钩子函数中进行，利用`axios().then()`异步加载数据，并执行首次轮播图动态展示；  
    - 轮播图的动态展示，使用`setInterval(()=>{},interval)`定时器制作，与此对应`clearInterval()`清除定时器；  
    - 使用`v-for`来动态遍历图片和indicator进行展示；  
    - `v-show`判断要展示的照片，`v-bind:class`配合三元运算符来动态展示indicator；  
    - 要使用的监听事件有：`click`、`mouseenter`、`mouseleave`；  
  3、笔记：  
    - CSS样式笔记  
       ```css
          /*块级居中*/
          margin：0 auto；
          /*垂直居中，子相父绝*/
          position:absolute;
          top:50%;
          transform:translate(0,-50%)
          /*利用i标签制作箭头*/
          display: inline-block;
          width: 6px;
          height: 6px;
          border-top: 2px solid #fff;
          border-left: 2px solid #fff;
          transform: rotate(-45deg);
       ```
 
