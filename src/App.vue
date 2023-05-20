<template>
  <section v-if="hasFruit">
    <h1>Fruits</h1>
    <ul>
      <li v-for="fruit in fruits" :key="fruit">{{ fruit }}</li>
    </ul>
  </section>
  <section>
    <h1>Reverse Fruits</h1>
    <ul>
      <li v-for="fruit in reverseFruits" :key="fruit">{{ fruit }}</li>
    </ul>
  </section>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <h1 @click="increase"> count : {{count}}</h1>
  <h1 v-once @click="add">{{ msg }} </h1>
  <p v-bind:class="msgStyle" v-html="msgHtml"></p>
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
      fruits: ['Apple', 'Banana', 'Cherry'],
      msg: 'Hello taekyung',
      msgHtml: '<div sycle="color: red;">Hello!!</div>',
      msgStyle: 'active'
    }
  },
  computed: {
    hasFruit(){
      return this.fruits.length > 0
    },
    reverseFruits() {
      return this.fruits.map(fruit => {
        return fruit.split('').reverse().join('')
      })
    }
  },
  beforeCreate(){
    console.log('Before Create', this.count)
  },
  created(){
    console.log('Created!', this.count)
    console.log(document.querySelector('h1'), 'created에서는 연결이 안되어서 없음')
  },
  beforeMount() {
    console.log('Before mount')
  },
  mounted(){
    console.log('Mounted')
    console.log(document.querySelector('h1'), 'mounted상태에서 연결되어 데이터 나옴')
  },
  methods: {
    increase(){
      this.count += 1
    },
    add() {
      this.msg += '!'

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
.active{
  color: rgb(168, 112, 51);
  font-size: 15px;
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
