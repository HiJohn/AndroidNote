
---

1. Android 应用的整个生命周期，由其组件的生命周期组成 ，随着用户在各个界面切换，每个界面都经历“生死”的转换， 如Application，Activity ，Fragment，都有onDestroy方法，进入此方法后他们生命周期结束，应该被回收。
`
`
2.然后我们需要解决：如何得到未被回收的对象。ReferenceQueue+WeakReference+手动调用 GC可实现这个需求。

`  WeakReference 创建时，传入一个 ReferenceQueue 对象。 
当被 WeakReference 引用的对象的生命周期结束，一旦被 GC 检查到，GC 将会把该对象添加到 ReferenceQueue 中，待ReferenceQueue处理。
当 GC 过后对象一直不被加入 ReferenceQueue，它可能存在内存泄漏。`

3.找到了未被回收的对象，如何确认是否真的内存泄漏？这里可以将问题转换为：未被回收的对象，是否被其他对象引用？找出其最短引用链。VMDebug + HAHA 完成需求。	

`	VM 会有堆内各个对象的引用情况，并能以hprof文件导出。
HAHA 是一个由 square 开源的 Android 堆分析库，分析 hprof 文件生成Snapshot对象。
Snapshot用以查询对象的最短引用链。`

