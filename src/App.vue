// Top level component that serves as the
// framework for the entire application

// Template Section
// Visual part of the component
<template>
  <div>
    <!-- render the TodoList compoent - note that camelcase (TodoLis) is changed to snakecase (todo-list) -->
    <todo-list></todo-list>
  </div>
</template>

// Component Class Section
// Behaviour, events, data storage part of the component
<script>
// import our component
import TodoList from './components/TodoList'

export default {
  // reference to the TodoList component in the compoents property
  components: {
    TodoList
  }
}
</script>

// Style Section
// Improve the appearance of the template within the component
<style>
</style>
