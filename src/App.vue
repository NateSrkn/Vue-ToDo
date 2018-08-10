<template>
  <div id="app">
    <to-do-list v-bind:todos="todos" :key="todos.id" />
  </div>
</template>

<script>
import toDoList from './components/toDoList.vue'
import toDoData from './assets/todos.js'

export default {
  name: 'app',
  components: {
    toDoList,
  },
  data() {
    return {
      todos: toDoData,
    }
  },
}
</script>

<style lang="scss">

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

i {
    cursor: pointer;
}

.card {
  width:318px;
}

</style>
