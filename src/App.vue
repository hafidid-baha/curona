<template>
  <div class="container mt-5">
    <WorldState />
    <ContryState class="mt-2" />
    <div class="row justify-content-center mt-3">
        <div class="col-6 text-center text-white mb-3">By Hafid id-baha</div>
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import WorldState from './components/WorldState.vue'
import ContryState from './components/ContryState.vue'

export default {
  name: 'App',
  components: {
    WorldState,ContryState
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Cairo&display=swap');
#app {
  font-family: 'Cairo', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
html,body{
  font-family: 'Cairo', sans-serif;
  background: #846b6b;
}
</style>
