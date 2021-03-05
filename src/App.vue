<template>
  <div id="app">
     <todo-card></todo-card>
  </div>
</template>

<script>
import todoCard from './components/todo-card.vue'
export default {
  components: { todoCard },
  name: 'app',
  data () {
    return {
      msg: 'Hello, et bienvenue sur la demo TodoList en Vue.js!'
    }
  }
}
</script>

<style>
  #app {
    padding-top: 100px;
  }

  body {
    background-color: rgb(255, 187, 0);
    min-height: 100vh;
  }
</style>