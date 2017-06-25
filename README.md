# js-event-loop
js事件循环机制

JavaScript代码的执行过程中，除了依靠函数调用栈来搞定函数的执行顺序外，还依靠任务队列来搞定另外一些代码的执行

一个线程中，事件循环是唯一的，但是任务队列可以拥有多个

任务队列又分为宏任务与微任务

宏任务包括：script(整体代码), setTimeout, setInterval, setImmediate, I/O, UI rendering。

微任务包括：process.nextTick, Promise, Object.observe(已废弃), MutationObserver(html5新特性)

事件循环的顺序，决定了JavaScript代码的执行顺序。

它从script(整体代码/宏任务)开始执行第一次循环。之后全局上下文进入函数调用栈。

直到调用栈清空(只剩全局)，然后执行所有的微任务。当所有可执行的微任务执行完毕之后。循环再次从宏任务开始，

找到其中一个任务队列执行完毕，然后再执行所有的微任务，这样一直循环下去。

其中每一个任务的执行，无论是宏还是微，都是借助函数调用栈来完成。

http://www.jianshu.com/p/12b9f73c5a4f
