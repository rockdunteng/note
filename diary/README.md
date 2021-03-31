<meta name="referrer" content="no-referrer"/>
# 每日记录

## 2019-07-05 

- 学习了渡一的Vuex，并整理了[笔记和代码](https://github.com/Dunteng/learnVue/tree/master/%E5%AD%A6%E4%B9%A0Vuex)
- 学习了 严格模式
  - [谈谈 JS 中的严格模式](https://segmentfault.com/a/1190000004482420)
  - [前端开发必须知道JavaScript中的严格模式](http://www.ruanyifeng.com/blog/2013/01/javascript_strict_mode.html)

<br><br>

## 2019-09-20

- 复习了 axios 的知识，将其补充了进了 vue 的笔记，👉[点击](http://dunteng.xin/[object%20Object]2019/08/09/vue%E7%9F%A5%E8%AF%86%E7%82%B9.html)
- [axios 中文说明](https://www.kancloud.cn/yunye/axios/234845)
- 发现一个很好的前端知识网页，👉[点击](http://doc.liangxinghua.com/)

<br><br>

## 2020-03-16

- 编程题

  ```js
  		// 编写一个函数，如果数组中有一个数字出现的次数超过数组长度的一半，返回这个数字，
  		// 如果不存在，返回0。
  
  		(function dunteng(arr) {
  			let tempObj = {}
  			let result = 0
  			arr.forEach(element => {
  				console.log(element);
  				if (tempObj[element] > 0) {
  					tempObj[element]++;
  				} else {
  					tempObj[element] = 1
  				}
  				if (tempObj[element] > arr.length / 2) {
  					result = element
  				}
  			});
  			console.log(tempObj);
  			console.log(result);
  			return result
  		})([6, 6, 6, 45, 78])
  ```


## 2020-03-19

- JavaScript数组方法中 find 和 filter 方法的区别

  ```js
  let kkk = [12,54,6,78,3]
  kkk.find(g=>g>10)  //输出结果为12，原数组kkk不改变
  
  kkk.filter(g=>g>10)  //输出结果为一个数组[12, 54, 78]，原数组kkk不改变
  ```

  array.find(fn) 和 array.filter(fn) 都不改变原数组，前者返回满足参数函数的第一个元素，否则返回undefined；后者返回满足参数函数的所有元素形成的数组，否则返回空数组。

- [Vue中过滤器传参](https://blog.csdn.net/q95548854/article/details/95173914)

- [lodash工具库](http://lodash.think2011.net/getting-started)

  对后台返回的数据进行去重。使用一个插件[lodash](http://lodash.think2011.net/getting-started)进行数据去重👇

  ```js
  import _ from 'lodash';
  
  state.NoticeList = _.uniqBy(payload, 'id');//uniqBy这个方法可以去重
  ```

  这是我在之前在写sfa项目时用lodash来进行数据去重，当然它还有其他更强大的功能。

- [vue状态动画](https://cn.vuejs.org/v2/guide/transitioning-state.html?)

  在项目的/public/index.html中`<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/1.20.3/TweenMax.min.js"></script>`引入了这个库。然后像👇这样使用：

  ```js
   TweenLite.to(this.sailes, 1, res.data); 
  ```

  我在sfa项目中用了这个库，是在实现“店铺活动”页面中的数据和进度条动态变化的效果。

- JavaScript toFixed() 方法

  把数字转换为字符串，结果的小数点后有指定位数的数字，且具有四舍五入效果：

  var num = 5.56789;
  var n=num.toFixed(2);

  *n* 输出结果:

  5.57

<br><br>

## 2020-03-20

- [input标签的oninput事件和onchange事件的区别](https://www.cnblogs.com/xuzhudong/p/8630610.html)
  - 我在sfa项目中的签到页面，里面要添加图片，我用`<input @change="uploadImg" type="file" accept="image/*" class="input-file" ref="file" />`来做，其中图片选好后就会自动触发@change事件。



- 添加图片功能

  - 先封装一个组件src\components\ImgBtn.vue，这个组件可以是“添加图片”也可以是“删除图片”。

    如何使点击“添加图片”的时候打开系统的照片文件夹？

    这里用 

    ```html
    <input @change="uploadImg" type="file" accept="image/*" class="input-file" ref="file" />
    ```

    来实现打开文件夹添加图片的功能，**但是我们把这个input隐藏起来了，希望点击imgBtn组件的时候可以调用input的事件。**

    ```html
    <ImgBtn
            @click="$refs.file.click()"
            class="img-box"
            :isred="false"
            iconclass="icon-xiangji"
            val="添加照片"
          ></ImgBtn>
    ```

    **这里的`$refs.file.click()`很关键。**最后通过 `console.log(this.$refs.file.files[0])`可以获得我们选取的文件。

    以上是我在SFA项目的src\views\SignIn.vue中的应用

- .env VUE的环境变量

  [官网文档](https://cli.vuejs.org/zh/guide/mode-and-env.html#%E5%9C%A8%E5%AE%A2%E6%88%B7%E7%AB%AF%E4%BE%A7%E4%BB%A3%E7%A0%81%E4%B8%AD%E4%BD%BF%E7%94%A8%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F)

  我在项目根目录新建了一个文件`.env`，内容如下：

  ```
  VUE_APP_BASEURL=http://localhost:8889
  ```

  必须是以`VUE_APP_`开头，这里我定义了一个baseurl。

  然后在src\views\SignIn.vue中获取到👇

  ```js
  process.env.VUE_APP_BASEURL
  ```

  这里是在我签到的图片上传之后，需要显示在当前页面，由于开发时使用的基本url是http://localhost:8889，但是在上线的时候很大可能不是这个url，那么就要手动去修改代码中的所有url，这样很麻烦，所以引入vue的环境变量功能，就像上面所示。



- [搜索框封装组件如何也实现v-model同步data中的数据？](https://dunteng.github.io/2020/03/04/inputcomponentv-model.html)



<br><br>

## 2020-03-21

- [Vuex-persistedstate](https://www.npmjs.com/package/vuex-persistedstate)  持久化插件-解决刷新数据消失的问题

  - 现象如下图所示：

    ![]()

  - 其实也可以自己手动存入缓存中，但是既然有现成的插件，就直接用好了，方便。

  - 我在sfa项目中有用到

  - 参考文章： [文章一](https://juejin.im/post/5b62999fe51d4519610e336e)   [文章二](https://juejin.im/post/5d01fa7e6fb9a07ebb052df3)



- 数组添加新数据除了用push，还可以用arr = [...arr, ...newData]这种扩展运算符的方式。最近一直用后者，逼格比较高。

<br><br>

## 2020-03-22

- [v-model的修饰符](https://cn.vuejs.org/v2/guide/forms.html#%E4%BF%AE%E9%A5%B0%E7%AC%A6)

  - v-model.number的坑

    我们知道在input标签中用v-model双向数据绑定的时候，虽然输入框输入的是数字，最终打印输出的时候却是字符串类型。为了解决这个问题，除了手动用parseint进行转化之外，还可以直接使用v-model.number这个修饰符，这样输出的结果就是number类型了，但是它有坑：[一、精度问题](https://blog.csdn.net/cmchenmei/article/details/82423864)， [二、汉字问题](https://blog.csdn.net/A13330069275/article/details/85598664)

- ### Mutation 需遵守 Vue 的响应规则

  既然 Vuex 的 store 中的状态是响应式的，那么当我们变更状态时，监视状态的 Vue 组件也会自动更新。这也意味着 Vuex 中的 mutation 也需要与使用 Vue 一样遵守一些注意事项：

  1. 最好提前在你的 store 中初始化好所有所需属性。
  2. 当需要在对象上添加新属性时，你应该

  - 使用 `Vue.set(obj, 'newProp', 123)`, 或者

  - 以新对象替换老对象。例如，利用[对象展开运算符](https://github.com/tc39/proposal-object-rest-spread)我们可以这样写：

    ```js
    state.obj = { ...state.obj, newProp: 123 }
    ```

<br><br>

## 2020-03-23

- [vue里面父组件如何修改子组件样式](https://blog.csdn.net/csdn_yudong/article/details/79087236)

- router的按需加载。如果组件依赖的东西非常多，建议使用按需加载；否则建议直接引用。因为如果是按需加载，在打包的时候，按需加载的组件会单独生成对应的js文件，如果所有组件都是按需加载的方式同时这些个组件并不是很庞大和多依赖，打包生成的多个js文件所形成的加载开销其实是大于直接引用组件所造成的压力的，很不划算。

- CDN引入减小包大小

  项目将vue 、vue-router、lodash等进行了改用CDN引入的方式从而减少了打包后的文件大小。

  在vue.config.js中进行如下配置：

  ```js
    configureWebpack: config => {
      config.externals = {
        vue: 'Vue',
        'vue-router': 'VueRouter',
        lodash: {
          commonjs: 'lodash',
          umd: 'lodash',
          root: '_'
        }
      };
    }
  ```

  （关键就是这个externals👆）

  然后在模板文件public/index.html中引入CDN链接。

  ![](https://pic4.zhimg.com/v2-b7d1a0a563a00bf73d62bd52108d6443_r.jpg)

- 骨架屏

  - 最古老的方式是手动在模板页面中手写骨架屏代码，这样很呆板且不实用
    - 我在sfa项目中就是在模板文件public/index.html中写一个骨架屏代码和样式。在页面还没加载出来的时候先显示出这个骨架屏页面，改善用户等待首屏加载的体验
  - 使用自动生成骨架屏的插件
  - 让UI画好骨架屏图片（我觉得这个最棒

