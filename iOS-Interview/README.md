
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
- 如何去选择使用不同的锁
```
https://juejin.im/post/5e7ab7755188255e1a15baf9
[不再安全的 OSSpinLock](https://blog.ibireme.com/2016/01/16/spinlock_is_unsafe_in_ios/)
看场景，多读还是多写，还是同时读写
```
- [自选锁优先级反转问题及解决方案](https://blog.csdn.net/Kendiv/article/details/1788966)

### 网络
- 浏览器输入网址到页面完全加载出来都发生了什么

### 大前端
- 对大前端技术的理解
