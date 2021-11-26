
## 1.v-for 是 key 的作用？

- 唯一标识。

## 2. key 原理？(index作为key)

- 真实DOM 与 虚拟DOM 对比。
  1. 初始数据；
  2. 根据数据生成VDOM，key分别是 0...index；
  3. 当数据发生改变时；
  4. 根据新数据 生成新VDOM；
  5. 新、旧VDOM 进行对比（依赖key值）；
  

  

