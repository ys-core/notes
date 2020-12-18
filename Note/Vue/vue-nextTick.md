

nextTick 涉及到的知识是 Vue中的DOM更新是异步的

1. 在created()钩子执行时DOM并未进行任何渲染,此时DOM操作无异于徒劳,所以一定要将DOM操作的js代码放入到Vue.nextTick()的回调函数中去
    与之对应的mounted()钩子函数在执行的时所有的DOM的挂载和渲染都已经完成

2. 在数据变化后要执行的某个操作,而这个操作选哟使用随数据变化而改变的DOM结构的时候,这些操作都应该放进Vue.nextTick()中