
# iOS Interview

- [大内存分配的监控和与其他方案的比较优劣](https://youtu.be/I6ENT_OB7Js)
- 启动优化处理方案
- object 加入数组如何不增加引用计数(答案方向: NSHashTable)
```
NSHashTable NSMapTable NSPointArray 对应 set dict array

```
- +load 和 +initialized 的区别
- 怎么找到 +load 中的所有方法
- Mach-O 中都有什么东西
- 版本号校验的实现
- 做过哪些与性能优化相关的工作？
- [iOS 触摸事件原理](https://www.jianshu.com/p/c294d1bd963d?utm_campaign=hugo&utm_medium=reader_share&utm_content=note&utm_source=weixin-friends)
- [weak 底层原理](https://github.com/qing-song/Blog/blob/main/iOS-Interview/Resource/weak%20%20底层原理.pdf)
- AutoLayout 有没有用过
- leading 和 left 的区别
- Swift 和 Objective-C 混编注意事项
- [class方法和objc_getClass方法有什么区别](https://www.jianshu.com/p/fea799096cf7)

### 锁及线程
- 信号量的加加减减是怎么实现的，怎么保证线程的安全，锁的种类有哪些
- 如果不用锁的话，怎么实现线程同步，线程同步什么意思，
- 如何去选择使用不同的锁
```
https://juejin.im/post/5e7ab7755188255e1a15baf9
[不再安全的 OSSpinLock](https://blog.ibireme.com/2016/01/16/spinlock_is_unsafe_in_ios/)
看场景，多读还是多写，还是同时读写
```
- [自选锁优先级反转问题及解决方案](https://blog.csdn.net/Kendiv/article/details/1788966)
- [GCD 之 底层原理分析](https://www.jianshu.com/p/693ec962b3d3)

### 
- 宏定义的原理
- 内存泄漏的场景，线上的内存泄漏怎么处理，怎么通知
- forwardTargetSelector 能够返回自己吗？
- 怎么计算 UIIMage 的大小
- 显示动画，隐式动画的区别，单独设置 View.layer 的属性，能够触发隐式动画吗？
- 怎么计算一个 View 的真是曝光，相对坐标和视图大小够了吗？
- KVC 原理，ValueForKey 按照怎样的流程查找属性的
- 不用 dispatch_once 来实现一个单利
- 一个图片是怎么展示在屏幕上的
- lottie 的实现原理
- 不用 AppCode 怎么检查有没有未调用的方法，自己是否可以设计一个方案

### 网络
- 浏览器输入网址到页面完全加载出来都发生了什么

### 大前端
- 对大前端技术的理解
