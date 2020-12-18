

Vue

---------------------------------------2016.6.11---Wendesday----------------------------------------

1.  Vue中new Vue({el:"#app"....}) 中的#app指的是index.html中的#app非App.vue中的,看页面中的source code或者更改index.html中的#app可以验证

2.  index.html中的#app指定绑定目标，而App.vue中的#app提供填充内容，两者在运行时指的是同一个DOM元素

3.  css动画不同于css过渡，在动画中v-enter类名的节点插入到DOM后不会立即删除,而是在animationed事件触发时删除


@keyframes aslide{
	0{
	
	}
	50%{
	
	}
	100%{
	
	}
}

4. Vue中同时使用过渡和动画时，时间由指定的type="transition"还是type="animation"决定,

5. 自定义过渡类名 enter-class, enter-active-class,enter-to-class,leave-class,leave-active-class,leave-to-class,优先级高于普通类名

6. Vue为了知道过渡的完成,必须设置相应的事件监听器，它可以是transitioned或animationed,这取决于给元素应用的css规则,使用其中一种,Vue将自动识别并设置监听

7. JavaScript钩子

<transition
	v-on:before-enter="beforeEnter"
	v-on:enter="enter"
	v-on:after-enter="afterEnter"
	v-on:enter-cancelled="enterCancelled"

	v-on:before-leave="beforeLeave"
	v-on:leave="leave"
	v-on:after-leave="afterLeave"
	v-on:leave-cancelled="leaveCancelled"
>

enter: function (el, done) {
    // ...
    done()
},
  
leave: function (el, done) {
    // ...
    done()
},

当只使用JavaScript过渡的时候,在enter和leave中必须使用done进行回调,否者,它们将被同步调用,过渡会立即完成,并且推荐在只使用JavaScript过渡的元素时添加
v-bind:css="false",Vue会跳过CSS的检测,这也可以避免过渡过程中CSS的影响

















