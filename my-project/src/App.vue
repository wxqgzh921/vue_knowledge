<template>
  <div id="app">
    <img src="./assets/logo.png">
    <HelloWorld/>
    <button @click="toshow">点击显示某一个子组件</button>
    <component v-bind:is="which_to_show"></component>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import IsOne from './components/isone'
import IsTwo from './components/istwo'

export default {
  name: 'App',
  data(){
    return{
      which_to_show:"first"
    }
  },
  components: {
    HelloWorld,
    first:IsOne,
    second:IsTwo
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
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
