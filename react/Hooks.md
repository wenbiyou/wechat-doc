## Hooks
- Hooks的作用：一套能够使函数组件更强大、更灵活的“钩子”


## 类组件&函数组件
- 类组件 -> 功能多且大，是一个重装战舰，面向对象编程
- 函数组件 -> 轻量灵活，函数组件能捕获render内部状态，真正把数据和渲染绑定在一起，函数式编程

## 钩子
- useState(initState) 为函数组件引入state，一个useState对应一个单独的状态
- useEffect(callback, []) 允许函数组件引入副作用，弥补生命周期的缺失
  - 返回的函数作为清除函数，在卸载时触发清除函数

## 为什么需要Hooks
- 告别难以理解的class [this, 生命周期（学习成本、不合理规范模式）]
- 解决业务逻辑难以拆分的问题 [逻辑常混合在生命周期里]
- 使状态逻辑的复用变得简单
- 函数组件从设计思想看，更切合React的理念（把数据和渲染绑定一起）

## Hooks的局限性
- Hooks目前还不能完全地为函数组件补齐类组件的能力
- Hooks在使用层面有着严格的规则约束
- 轻量是函数组件的基因，这可能使它不能够很好的消化复杂

## Hook的本质是链表


## 简介
- 没有破坏性改动
  - 完全可选
  - 100% 向后兼容
  - 现在可用
  - 没有计划从React中移除class
- 动机
  - Hook 使你无需修改组件结构的情况下复用状态逻辑
  - Hook 将组件中相互关联的部分拆分成更小的函数，而非强制按照生命周期划分
  - Hook 使你在非class的情况下提供更多的react特性
- Hook 规则
  - 只在最顶层使用Hook
  - 只在React函数中调用Hook
- Hook Api
  - useState
  - useEffect
  - useContext

  - useReducer
  - useCallback
  - useRef
  - useMemo
  - useLayoutEffect
  - useDebugValue

