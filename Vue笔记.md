
[toc]

# Vue重点筛选

## 一、Vue事件修饰符

1. stop：阻止事件的冒泡（继续传播）
2. pervent：阻止默认（如a标签的跳转，submit事件的跳转）
3. capture：事件监听器为捕获模式（即先处理capture元素事件，然后处理其内部事件）
4. self：event.target当前元素触发
5. once：事件只触发一次
6. passive：元素的默认事件先触发，再执行编写的事件内容（较多的是scrool、wheel事件）

## 二、键盘事件

>v-on:keyup / v-on:keydown 监听键盘事件

### 1. Vue常见的系统键盘别名

- @keyup.enter => 回车
- @keyup.delete => delete键 和 退格键
- @keyup.space => 空格
- @keydown.tab => Tab键+配合keydown使用
- @keyup.up => 上
- ...

### 2. Vue 未提供别名的按键

- 可以使用按键原始的key去绑定，注意要转为kebab-case 短横先命名；
- 可以用按键原始的keyCode去绑定，@keyup.13 对应的是enter键（**未来会摒弃**）

### 3. 系统修饰键（可用于复合按键）：ctrl/alt/shift/meta

- 配合 **keyup** 使用：按下修饰键+再按下其他键，然后释放，事件才触发；
  > 如：@keyup.ctrl.l => 指 按下ctr+l 后 触发事件； 

- 配合 **keydown** 使用：正常触发键事件

## 三、计算属性 computed

### 1. 什么是属性？计算属性？

- 在 vue 中，认为 data 中的数据就是属性；
- 计算属性：就是对已经定义的“属性”进行加工，生成新的属性就是计算属性；

### 2. 如何定义计算属性？

- computed 属性的完整的写法：

  ```javascript
    computed:{
      fullName:{
        get(){
          //此处的 this 是 vm 
          return this.firstName + this.lastName;
        },
        set(value){
          //set 非必须要写；
        }
      }
    }

  ```
- computed 简写形式
  set()省略。

  ```javascript
    computed:{
      fullName(){

      }
    }
  ```

### 3. computed 的特点？

- 与 methods 相比，**有缓存**
  - 初始读取fullName属性时，get会被调用；
  - 所依赖的值（firstName/lastName）改变时，get被调用
- 与 watch 相比，**页面初始化时，就立即调用**

## 四、监听属性 watch

