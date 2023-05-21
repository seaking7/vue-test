<template>
    <h3 ref="hello">{{ msg }}</h3>
    <input type="text" v-model.lazy.trim="msg" />
    <ul>
      <li v-for="(f,i) in fruits" :key="f">{{ f }}-{{ i }}</li>
    </ul>
    <ul>
      <li v-for="{id, name} in newFruits" :key="id">{{ name }}-{{ id }}</li>
    </ul>
    <section v-if="hasFruit">
      <h1 :style="[fontStyle, backgroundStyle]"
      @click="changeStyle">Fruits</h1>
      <ul>
        <li v-for="fruit in fruits" :key="fruit">{{ fruit }}</li>
      </ul>
    </section>
    <section>
      <h1 @click="handler">Reverse Fruits</h1>
      <ul v-if="isShow">
        <li v-for="fruit in reverseFruits" :key="fruit">{{ fruit }}</li>
      </ul>
      <ul v-else><li>not found</li></ul>
    </section>
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->

  </template>



<script>
import shortid from 'shortid'

export default {
  data(){
    return {
      count: 2,
      fruits: ['Apple', 'Banana', 'Cherry'],
      msg: 'Hello taekyung',
      msgHtml: '<div sycle="color: red;">Hello!!</div>',
      msgStyle: 'active',
      isShow: true,
      fontStyle: {
        color: 'orange',
        fontSize: '30px'
      },
      backgroundStyle: {
        backgroundColor: 'black'
      }
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
    },
    newFruits() {
      return this.fruits.map((fruit) => ({
        id: shortid.generate(),
        name: fruit
      }))
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
    console.log(this.$refs.hello)
    console.log(document.querySelector('h1'), 'mounted상태에서 연결되어 데이터 나옴')
  },
  methods: {
    increase(){
      this.count += 1
    },
    add() {
      this.msg += '!'
    },
    changeStyle(event) {
      this.fontStyle.color = 'red'
      this.fontStyle.fontSize = '50px'
      console.log(event)
    },
    handler(event) {
      this.isShow = !this.isShow
      console.log(event)
    },
    keyHandler(event) {
      if(event.key === 'Enter'){
        console.log('Enter!!')
      }
    },
    inputHandler(event) {
      this.msg = event.target.value
      console.log(this.msg)
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
