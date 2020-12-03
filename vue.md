# 自定义对象响应

1. 自己创建的obj属性不会响应dom样式改变
2. 因为自己创建的obj属性没有vue的get和set方法

3. 需要使用vue的$set方法来创建新的属性

4. 或者使用Object.assign({},vue对象,{添加的对象})

5. Ooject.assign可以把对象的所有属性添加到新对象当中


# 使用props接受参数

```
// 必须是用name才能使用params传参
// 如果是用路径跳转的化，需要使用query传参但无法是用props接收
this.$router({
	name: 'asd',  
	params:{
	
	}				
})

 {
    path: '/item1/:id',
    name: 'item1',
    component: () => import('../pages/test/item1.vue'),
    props: true // 标准模式
    props:{
      yes: true // 当 props 是静态的时候有用
    }
    props:{
    	getTime: (() => new Date())() // 函数模式
    }
  },
  {
    path: '/item2',
    name: 'item2',
    component: () => import('../pages/test/item2.vue'),
    props: true,
    
  }

```

