<template>
  <div id="app">
   <TodoCard />
  </div>
</template>

<script>
import TodoCard from './components/TodoCard.vue'
export default {
  name: 'App',
  components: {
    TodoCard
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
</style>
