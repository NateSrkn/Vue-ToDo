<template>
  <div>
      <div class="row">
          <h5 class="col s6 center-align">Finished: {{todos.filter(todo => {return todo.isComplete === true}).length}}</h5>
          <h5 class="col s6 center-align">Incomplete: {{todos.filter(todo => {return todo.isComplete === false}).length}}</h5>
      </div>
      <div class="row">
         <add-to-do v-on:add-to-do="addToDo" v-bind:isAdding="isAdding" />
         <toDo v-on:delete-to-do="deleteToDo" v-for="todo in todos" v-bind:todo="todo" :key="todo.id" />
      </div>
  </div>
</template>

<script>
import toDo from "./toDo"
import addToDo from "./addToDo"


export default {
  props: ['todos'],
  components: {
    toDo,
    addToDo
  },
  methods: {
    deleteToDo(todo) {
      const tIndex = this.todos.indexOf(todo);
      this.todos.splice(tIndex, 1);
    },
    addToDo(todo) {
      this.todos.push(todo)
    }
  }
}
      
</script>
