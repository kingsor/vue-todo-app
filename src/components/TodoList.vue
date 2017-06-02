<template>
<div>
    <p class="tasks">Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p class="tasks">Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    <todo v-on:complete-todo="completeTodo" v-on:delete-todo="deleteTodo"  v-for="todo in todos" v-bind:todo="todo"></todo>
</div>
</template>

<script type="text/javascript">

import Todo from './Todo'

export default {
  props: ['todos'],
  components: {
    Todo
  },
  methods: {
    deleteTodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos.splice(todoIndex, 1)
    },
    completeTodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      console.log('todoIndex -> ' + todoIndex)
      this.todos[todoIndex].done = true
    }
  }
}
</script>

<style scoped>
p.tasks {
  text-align: center;
}
</style>
