// TodoList component

// Template Section
// Visual part of the component
<template>
<div>
  <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
  <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
  <!-- Pass data to the Todo component to render the Todo list -->
  <!-- Event handler which will trigger the completTodo or deleteTodo method -->
  <todo v-on:complete-todo="completeTodo" v-on:delete-todo="deleteTodo" v-for="todo in todos" v-bind:key="todo.title" :todo="todo" ></todo>
</div>
</template>

// Component Class Section
// Behaviour, events, data storage part of the component
<script type = "text/javascript" >
// import our component
import Todo from './Todo'

export default {
  props: ['todos'],
  // reference to the Todo component in the compoents property
  components: {
    Todo
  },
  // Event handler to handle the delete
  methods: {
    deleteTodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos.splice(todoIndex, 1)
    },
    completeTodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos[todoIndex].done = true
    }
  }
}
</script>

// Style Section
// Improve the appearance of the template within the component
<style>
</style>
