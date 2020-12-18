


-----------------------------------2019.06.05----三--------------------------------

1.路由守卫 | 全局守卫      router.beforeEach/router.beforeResolve/router.afterEach
           | 路由独享守卫  beforeEnter
		   | 组件内守卫    beforeRouteEnter/beforeRouteUpdate/beforeRouteLeave
    
	beforeRouteLeave() ====> router.beforeEach()  ====> beforeEnter()   ======> beforeRouteEnter  ====>  router.beforeResolve() ====> 
	router.afterEach() ====> beforeCreate() ==== > created()  ====> beforeMount() ====> mounted() ====> beforeRouteEnter()中的next(),在该next中可以访问参见的vm实例对象

	beforeRouteEnter守卫不能访问this,因为守卫在导航确认前被调用，因此将登场的新组建还没被创建，值得注意的是
	beforeRouteEnter是支持给next传递回调的唯一守卫,对于beforeRouteUpdate和beforeRouteLeave来说，this已经可用了
	所以不支持传递回调，因为没有必要了
	
2.完整的导航解析流程
   1.  导航被触发
   2.  在失活的组件里调用离开守卫 beforeRouteLeave
   3.  调用全局的router.beforeEach守卫
   4.  在重用的组件里调用beforeRouteUpdate守卫
   5.  在路由配置里调用beforeEnter,即执行路由独享守卫
   6.  解析异步路由组件
   7.  在被激活的组件里调用beforeRouteEnter
   8.  调用全局的beforeResolve守卫
   9.  导航被确认
   10. 调用全局的router.afterEach守卫
   11. 触发DOM更新
   12. 用创建好的实例调用beforeRouteEnter守卫中传给next的回调函数
   
   beforeRouteEnter中的next()异步确实是在mounted()之后执行的
   
3.父子组件之间钩子执行顺序,假设当前路由是'/'
		router.beforeEach ----> beforeEnter ----> beforeRouteEnter ----> router.beforeResolve ----> router.afterEach ----> 
		beforeCreate(F) ----> created(F) ----> beforeMount(F) ----->  
		    beforeCreate(S) ----> created(S) ----> beforeMount(S) ---->  mounted(S)  ----->
		mounted(F) ----> F的beforeRouteEnter中的next()异步 ----> beforeUpdate(F/S) ----> updated(F/S)

   接下来假设从当前路由'/'跳转到'/test',并且'/test'对应组件无子组件,所有钩子的执行顺序为(接上)
	
       beforeRouteLeave ----> router.beforeEach ----> beforeEnter ----> beforeRouteEnter ----> router.beforeResolve ---->
	   router.afterEach ----> beforeCreate(T) ----> created(T) ----> beforeMount(T)  
	        beforeDestory(F) ----> beforeDestory(S) ----> Destoryed(S) ----> Destoryed(F) ---->
	   mounted(T) ----> T的beforeRouteEnter中的next()异步方法 ----> beforeUpdate(T) ----> updated(T)

4. 在beforeCreate()阶段,data,$el均为undefined,在create()阶段可以处理data,在mounted()阶段才可以处理dom


5. router-link中的tag属性可以设置为li,p等,默认为a



















   
   
   
   
   
   
   
   
   
   
   
   
   
   
	