// TodoList component

// Template Section
// Visual part of the component
<template>
<div>
  <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
  <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
  <!-- Pass data to the Todo component to render the Todo list -->
  <todo v-for="todo in todos" v-bind:key="todo.title" :todo="todo" ></todo>
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
  }
}
</script>

// Style Section
// Improve the appearance of the template within the component
<style>
</style>
