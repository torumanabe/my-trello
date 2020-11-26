<template>
  <div id="app">
    <board />
    <login />
  </div>
</template>

<script>
import Board from './components/Board.vue'
//import Login from './components/Login.vue'
export default {
  name: 'App',
  components: {
    Board,
    //Login
  }
}
</script>
