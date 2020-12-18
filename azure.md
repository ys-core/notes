
百纪世联
      azure@youngcaden.partner.onmschina.cn
	
      Tools0612
	  
	  
azure vm:


     azure
	 azureTools0612
	 
	 
	 
	 ip:   http://42.159.146.185/
	 
	 
Vue--slot:
	子组件模板至少包含一个插口，否则父组件的内容将会被丢弃，
	当子组件模板只有一个没有属性的slot时，父组件整个内容片段将插入到slot所在的DOM位置，并替换掉slot标签本身
	 
	作用域插槽的关键之处在于，父组件能够接受来自子组件的slot传递过来的参数
	 
	 
	 数据驱动、组件系统

const storeA = {
	state:{
	   count: 0,
	},
	getters:{},
	mutations:{
	   increment(State){
				state.count ++;
	   }
	},
	actions:{
		increment(context){
			context.commit('increment');
		}
	}

}
	 

const storeB = {
	state:{
	   count: 0,
	},
	getters:{},
	mutations:{
	   increment(State){
				state.count ++;
	   }
	},
	actions:{
		increment(context){
			context.commit('increment');
		}
	}

}
	 	
const store = new Vuex.Store({

	modules:{
		a: storeA,
		b: storeB
	}
})
		
	 
	 
	 
	 
	 
	 
	 
	 
	 
	 