## 1. Vue 系统 内置的指令

- v-on: 绑定事件指令...等常见
- v-text 
  - 作用：向其所在的节点中渲染 文本内容。
  - 与 插值语法 的区别是：v-text会替换掉节点中的文本内容，而插值语法不会；
  ```javascript
    <div>{{ name }}</div>

    <div v-text="name"></div>
  ```
- **v-html**
  - 与 v-text 相对比：v-html: 都会替换节点中的文本内容
  - 但是v-html 会将内内容语义化
  - **同时 v-html 存在 XSS 攻击**

- **v-cloak**
  - 本质是没有值
  - vue实例接管的一瞬间，**元素上的v-cloak属性就消失**，
- v-once
  - 当前元素**只动态渲染一次**，之后就是静态元素
- v-pre
  - 将文本原格式输出

## 2. Vue 自定义指令

### * 如何自定义指令v-big？

- 需要配置项：directives
 
  ```javascript
    //函数形式
    directives:{
      <!--big函数何时会被调用？1.指令与元素成功绑定时 2.模板重新渲染时 -->
      big(element,binding){

        <!-- element:当前的真实DOM节点 -->
        <!-- binding: 对象，主要使用到其value属性 -->

      }
    }

    //对象形式
    directives:{
      big:{
        bind(element,binding){

        },
        inserted(element,binding){

        },
        update(element,binding){

        }
        
      }
    }
  ```