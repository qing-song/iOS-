
# iOS Interview
- +load 和 +initialized 的区别
- 怎么找到 +load 中的所有方法
- Mach-O 中都有什么东西
- 版本号校验的实现
- 做过哪些与性能优化相关的工作？
- [iOS 触摸事件原理](https://www.jianshu.com/p/c294d1bd963d?utm_campaign=hugo&utm_medium=reader_share&utm_content=note&utm_source=weixin-friends)
- AutoLayout 有没有用过
- leading 和 left 的区别
- Swift 和 Objective-C 混编注意事项
- [class方法和objc_getClass方法有什么区别](https://www.jianshu.com/p/fea799096cf7)
- assign、strong 的区别，是否可以使用 assign 去修饰 NSObject？
- 如何实现NSNotification
- NSHashTable NSMapTable NSPointArray 对应 set dict array
- [iOS 编译过程原理](https://www.shuzhiduo.com/A/kjdwk306dN/)
- dSYM dwarfdump --lookup 地址 的原理是啥啊
- [iOS Crash分析必备：符号化系统库方法](https://zuikyo.github.io/2016/12/18/iOS%20Crash%E6%97%A5%E5%BF%97%E5%88%86%E6%9E%90%E5%BF%85%E5%A4%87%EF%BC%9A%E7%AC%A6%E5%8F%B7%E5%8C%96%E7%B3%BB%E7%BB%9F%E5%BA%93%E6%96%B9%E6%B3%95/)
- 有几张大图片 不经常更新 有活动的时候更新 我说用sd的缓存
```
看场景，SD memory 的缓存是 LRU 啊，你不更新，不就被 淘汰了么
```

### runtime
- runtime的三个核心机制
```
1）讲讲消息发送机制 （怎么找到这个方法去调用的）
2）讲讲消息转发机制
3）讲讲消息缓存机制
```
- 介绍一下 swizzle的步骤，具体到方法名，swizzle 不想替换父类，只想替换子类，怎么办
- Swizzle 的优缺点? 缺点会导致什么问题?
- 方法交换和分类同时去 hook 同一个方法，结果会怎么样？具体交换的是什么？交换时是如何处理参数的？
- 如果使用 NSInvocation的话，是否能处理方法和有返回值的场景？具体怎么实现的？
- ISA、类结构
- isa 指针是什么？里面有哪些特殊的位数？什么是TaggedPointer的优化？
- isa指针里面都存了什么，32和64位分别讲一下
- OC 是否支持重载? 为什么?
- IMP、SEL Method 都表示什么意思? 与 _cmd 相关
- class 的底层结构是什么样的？
- method_t 里包含什么？
- super 的本质是什么？
- OC的消息机制有几步？
- iOS的IMP方法寻址
- 方法缓存会存在哪里，类有多个对象时，方法会缓存多个还是一个
- block的理解，本质，底层结构
- Runloop 具体是一个什么东西  系统设计这个主要是为了解决什么问题呢 

### 内存
- iOS的强引用和弱引用是用来做什么的 
- [大内存分配的监控和与其他方案的比较优劣](https://youtu.be/I6ENT_OB7Js)
- 启动优化处理方案
- object 加入数组如何不增加引用计数(答案方向: NSHashTable)
```
NSHashTable NSMapTable NSPointArray 对应 set dict array
```
- Weak 表  的策略  
- nsobject对象  在 dealloc的时候系统做了什么处理
- [weak 底层原理，weak 是如何把对象重置为 nil 的](https://github.com/qing-song/Blog/blob/main/iOS-Interview/Resource/weak%20%20底层原理.pdf)
- AutoReleasePool 底层实现是怎样的，怎么实现及时释放的？子线程的释放时机是怎样的
- SideTable 底层结构是怎么样的
- 对象的 release 是怎么处理的
- 引用计数实现原理？引用计数表是如何维护的？
- alloc init new retain 源码是如何实现的
- tagpoint是否会释放？runtime通过什么标志来判断是不是tagpint？
- 堆和栈的区别，堆和栈是否会被线程所共享
- 内存空间中除了堆和栈还有什么内容
- 内存分配有几种方法
```
栈内存分配 alloca
 堆内存分配 calloc 、malloc+memset
```
- 在a线城创建一个对象, 在b线程的时候，它的count变成0了.那么它释放是在a线程还是在b线程释放的.也就是说它的那些内存回收是在a上做的还是b上的.
```
ARC 帮我们做了“谁创建、谁释放、谁引用、谁管理” 四个部分
```
- iOS 上虚拟内存如何保证没有碎片?介绍下虚拟内存的layout.
- 使用虚拟内存技术, 申请内存对应的物理内存区域是否连续的?
- [虚拟内存](https://zh.wikipedia.org/wiki/虚拟内存)
```
虚拟内存是计算机系统内存管理的一种技术。它使得应用程序认为它拥有连续可用的内存（一个连续完整的地址空间），而实际上物理内存通常被分隔成多个内存碎片，还有部分暂时存储在外部磁盘存储器上，在需要时进行数据交换。与没有使用虚拟内存技术的系统相比，使用这种技术使得大型程序的编写变得更容易，对真正的物理内存（例如RAM）的使用也更有效率。此外，虚拟内存技术可以使多个进程共享同一个运行库，并通过分割不同进程的内存空间来提高系统的安全性。
```
- [XNU之四：iOS虚拟内存限制](https://satanwoo.github.io/2018/01/14/iOS-virtual/)
- [iOS内存abort(Jetsam) 原理探究](http://satanwoo.github.io/2017/10/18/abort/)

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
- 触摸事件 发送到进程之前 经历了哪些流程 
- Springbod这种进程 具体是用来做什么 
- Runloop和内存、线程的一些关系  
- 观察者观察runloop的状态的 
- 使用runloop解决的一些case
- runloop卡顿检测 
- 模块化的过程中 主要做了哪些工作 出于什么样的设计和原则
- 业务层 注册路由 和 组件 

- 什么情况下做内存缓存 什么时候做一些磁盘缓存   用户无关的数据清理  
- 怎样计算图片占的内存空间 
- LRU Cache
- 性能监控的指标  
- 做一个报警   一分钟超过100次 报警系统   
- 虚拟内存的设计 

- 基础组件的抽离 解耦的拆分 仔细回答 
- 基础的东西都有哪些 
- 网络库用的是什么    Http请求到后端 然后渲染出来 说的详细一些
- 网络请求的线程是怎么管理的  发的是异步还是同步的 回调是在主线程 
- iOS应用启动之后，整个进程里面的内存是怎样划分的 
- OC  alloc一个对象 系统帮我们做了什么
- 创建一个线程时候，系统帮我们做了什么事情
- ARC
- 图片加载  内存缓存的是整个图片吗 还是做了什么处理 如果图片非常大 做了怎样的缓存处理 
- 图片缓存的移除策略  
- GET和POST有啥区别   POST的参数能放在url上吗 
- 整个网络的过程 怎样找到目标服务器 怎样传输    目标服务器怎样把数据返回的 他怎么知道是谁发出的请求
- 项目里有没有做过自定义的View 给图片加圆角  
- 代码里有没有遇到过循环引用的问题 
- Block是怎么实现的 
- 切换到主线程有哪些方式  
- Swift 对低版本的iOS系统是怎么兼容的
- Swift 相对于OC的好处  
- 应用里面crash 最多的情况是哪一个 
- Crash是怎么监控   bugly是怎么实现的   
- WKWebview 是怎么拦截的 会使用私有api吗 
- 拦截自定义scheme的时候 容器里面肯定是有网络请求的  跨域的问题是怎么解决的

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
- [iOS底层原理](https://www.cnblogs.com/gaoxiaoniu/category/1438437.html)
- label.textcolor = [UIColor redColor];过程发生了什么
- 请论述调用-[UITableView reloadData]过程发生了什么

### 项目相关
- 项目是不是组件化做的，怎么做的？
- 了解市面上组建化方案吗，为什么选的当前的组建化方案？
- 组件版本如何管理
- [基于桥的全量方法Hook方案](http://satanwoo.github.io/2017/09/24/mainthreadchecker1/)
- 热修复工具（JSPatch、火山引擎）

### 网络
- 浏览器输入网址到页面完全加载出来都发生了什么

### 大前端
- 对大前端技术的理解
- [小程序类的容器怎么实现的？](https://developers.weixin.qq.com/community/develop/article/doc/000c4e433707c072c1793e56f5c813)
```
同层渲染
```
- 2、JSBridge原理是什么？
- 3、让你监控网络优化成果，怎么弄？
- 4、WebView下载大图怎么优化？
