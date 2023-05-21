<template>

  <HelloWorld msg="Welcome to Taekyung"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {

  name: 'App',
  components: {
    HelloWorld
  },
  data(){
    return {
      count: 2,
      msg: 'Hello taekyung',
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
  created(){
    console.log('Created!', this.count)
    console.log(document.querySelector('h1'), 'created에서는 연결이 안되어서 없음')
  },
  mounted(){
    console.log('Mounted')
    console.log(document.querySelector('h1'), 'mounted상태에서 연결되어 데이터 나옴')
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
