<template>
  <div id="app">
    <HelloWorld />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style lang="scss" >
@import url('./assets/scss/normalize.scss');
#app{
  width: 100vw;
  height: 100vh;
}
</style>
