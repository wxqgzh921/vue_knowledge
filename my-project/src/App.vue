<template>
  <div id="app">
    <img src="./assets/logo.png">
    <HelloWorld>4353</HelloWorld>
    <!-- <button @click="toshow">点击显示某一个子组件</button>
    <keep-alive>
      <transition name="toshow">
        <component v-bind:is="which_to_show"></component>
      </transition>
    </keep-alive> -->
    <p>count:{{count}}</p>
    <button @click="setCount(count+1)"> {{count}} </button>
    <button @click="setCount(count-1)"> {{count}} </button>
    <p>{{user}}</p>
    <button @click="update">修改名字</button>
    <!-- <IsOne v-slot="{username}">{{ username.fristname}}</IsOne> -->
    <IsOne v-slot="slotProps">{{ slotProps.username.fristname}}</IsOne>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import IsOne from './components/isone'
import IsTwo from './components/istwo'
import {store,mutations} from './store'

export default {
  name: 'App',
  data(){
    return{
      which_to_show:"first",
      user:{
        name:'java',
        age:'20'
      }
    }
  },
  created(){
    const user = this.user;
    this.user = Object.freeze(user) //冻结了users的值,引用不会被冻结,我们需要reactive数据的时候，我们可以重新给users赋值。 (长列表性能优化：只是纯粹的数据展示，无需任何改动)
  },
  components: {
    HelloWorld,
    first:IsOne,
    second:IsTwo,
    IsOne
  },
  computed:{
    count(){
      return store.count;
    }
  },
  methods:{
    toshow(){
      var arr = ['first','second'];
      var index = arr.indexOf(this.which_to_show);
      console.log(index);
      if(index < 1){
        this.which_to_show = arr[index+1];
      }else{
        this.which_to_show = arr[0];
      }
      console.log(this.$children)
    },
    setCount: mutations.setCount,
    update(){
        this.user.name = 'c#'
    }
  }
}
</script>

<style>
@import './assets/css/animate.css';
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.toshow-enter-active{ animation: bounce-in .5s ; }
.toshow-leave-active{ animation: bounce-in .5s reverse; }
@keyframes bounce-in{
  0%{
    transform: scale(0);
  }
  50%{
    transform: scale(1.5);
  }
  100%{
    transform: scale(1);
  }
}
</style>
