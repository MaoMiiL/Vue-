
```javascript

  //Vue 定义组件：school
  var school = Vue.extend(options);

```

## 1. 关于VueComponent：

- school 组件本质是一个VueComponent的构造函数，且不是程序员自己定义的，是Vue.extend生成的；

- 我们只需要写 \<school>\</school>，Vue解析时会帮我们创建school组件实例对象，
  - 即帮我们执行：new VueComponent(options) 

- 特别注意：**每次Vue.extend 调用，返回的都是全新的VueComponent**；

- 关于 this 指向：
  - 组件配置中：
    - data函数，methods中的函数，watch中的函数，computed中的函数，它们的this均是【VueComponent实例对象】；
  - new Vue(options)配置中：
    - data函数，methods中的函数，watch中的函数，computed中的函数，它们的this均是【Vue实例对象】；

## 2.Vue中的内置关系

### （1）补充原型的知识
  ```javascript

    // Person.prototype 指向Person的原型对象 
    function Person() {
      
    }
    // person 是 Person的实例对象
    // person.__proto__ 指向的Person的原型对象
    var person = new Person();

    Person.prototype === person.__proto__ ; //true

  ```
### （2）内置关系
>&nbsp;
> VueComponent.__proto__.prototype === Vue.prototype;
>&nbsp;