
<template>
    <li>{{ name }}?!</li>
</template>
  
<script>
  export default {
    props: {
        name: {
            type: String,
            default: ''
        }
    }
  }
</script>
  
<style scoped>
  li {
    color: red;
  }
</style>
  