<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <h1 @click="increase"> count : {{count}}</h1>
  <div v-if="count > 4"> 4보다 큽니다!</div>
  <ul>
    <Fruit 
    v-for="fruit in fruits" 
    :key="fruit"
    :name="fruit">
    {{ fruit }}
  </Fruit>
  </ul>
  <HelloWorld msg="Welcome to Taekyung"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Fruit from './components/FruitData.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Fruit
  },
  data(){
    return {
      count: 2,
      fruits: ['Apple', 'Banana', 'Cherry']
    }
  },
  beforeCreate(){
    console.log('Before Create', this.count)
  },
  created(){
    console.log('Created!', this.count)
  },
  beforeMount() {
    console.log('Before mount')
  },
  mounted(){
    console.log('Mounted')
    console.log(document.querySelector('h1'))
  },
  methods: {
    increase(){
      this.count += 1
    }
  }
}
</script>

<style>
h1{
  font-size: 50px;
  color: royalblue;
}
ul > li {
  font-size: 30px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
