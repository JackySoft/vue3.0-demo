<template>
  <div id="app">
    <h1>{{title.name}}</h1>
    <div>{{user}}</div>
    <button @click="updateUser">修改名称</button>
    <div>当前count：{{computedCount}}</div>
    <button @click="increment">修改count</button>
  </div>
  <HellWorld msg="hello"></HellWorld>
</template>

<script>
import { reactive,ref,onMounted,computed } from 'vue'
import HellWorld from './components/HelloWorld.vue'
export default {
  name: 'App',
  components:{
    HellWorld
  },
  setup(){
    const title = reactive({
      name:'欢迎学习Vue3.0'
    })
    const user = ref('河畔一角');
    //如果需要修改值，可通过value
    
    const updateUser = ()=>{
      user.value = '河畔老师'
    }
    
    //生命周期方法
    onMounted(()=>{
      console.log('init mounted...')
    })

    // 初始化count值
    const count = ref(0);

    const increment = ()=>{
      count.value++
    }

    // 调用计算属性函数Hook
    const computedCount=computed(()=>count.value*10)

    return { title , user, updateUser,count,increment,computedCount }
  }
}
</script>

<style>
#app {
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
