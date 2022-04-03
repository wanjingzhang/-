- 对比

  与小程序的开发方式相比，React 显得更加现代化、规范化，而且 React 天生组件化更适合我们的业务开发，JSX 也比字符串模板有更强的表现力
  
- 生命周期

  onLaunch    componentWillMount 
  
  onLoad      componentDidMount
  
  onReady     componentDidMount
  
  onShow      不支持，需要特殊处理
  
  onHide      不支持，需要特殊处理
  
  onUnload    componentWillUnmount
  
- 数据更新方式
React setState 
小程序 setData 

- 事件绑定
React 是 onClick
小程序 bind + 事件名

- 巨大的差异
React 使用 JSX 来作为组件的模板
小程序 与Vue一样，是使用字符串模板

- 编译原理
  - Taro使用 babel 的核心编译器 babylon, 它支持对 JSX 语法解析，用JSX 构造新 AST，再将新 AST 进行递归遍历，生成小程序的模板。
  - Babel 的编译过程
      解析: 词法、语法分析，以及语义分析，生成符合 ESTree 标准 虚拟语法树(AST)
      转换: 针对 AST 做出已定义好的操作，babel 的配置文件 .babelrc 中定义的 preset 、 plugin 就是在这一步中执行并改变 AST 的
      生成: 将前一步转换好的 AST 生成目标代码的字符串
 
- 多端发布
   为了弥补不同端的差异，我们需要订制好一个统一的组件库标准，以及统一的 API 标准，在不同的端依靠它们的语法与能力去实现这个组件库与 API，同时还要为不同的端编写相应的运行时框架，负责初始化等等操作。只需要引入标准组件库 @tarojs/components 与运行时框架 @tarojs/taro ，代码经过编译之后，会变成对应端所需要的库。

- Redux 支持，
  在小程序端，Taro实现了 @tarojs/redux 这个库来作为小程序的 Redux 辅助库，并且以他作为基准库，它具有和 react-redux 一致的 API，在书写代码的时候，引用的都是  @tarojs/redux ，经过编译后，在 H5 端会替换成 nerv-redux（Nerv的 Redux 辅助库），在 RN 端会替换成 react-redux。

- 选Taro 做技术框架的原因
最近公司需要开发一款新的小程序，主要是做付费知识相关的产品，涉及到了虚拟商品支付，对于IOS的对于虚拟商品支付的种种限制，加上类似小程序的相关调研，决定IOS支付的方式走h5公众号支付绕开限制，所以在框架选型上面需要一套代码加一点兼容代码，就可以生成小程序和H5版本的库，考虑到本身技术栈以react为主，所以最后老大选择了Taro进行开发

   
