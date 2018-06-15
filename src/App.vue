// Top level component that serves as the
// framework for the entire application

// Template Section
// Visual part of the component
<template>
  <div>
    <!--
    // render the TodoList compoent - note that camelcase (TodoList) is changed to snakecase (todo-list)
    // pass data from the main compoent to the TodoList compoent by
    // using v-bind directive which takes an argument
    -->
    <todo-list v-bind:todos="todos"></todo-list>

    <!-- render the CreateTodo compoent - note that camelcase (CreateTodo) is changed to snakecase (create-todo) -->
    <create-todo v-on:create-todo="createTodo"></create-todo>
  </div>
</template>

// Component Class Section
// Behaviour, events, data storage part of the component
<script>
// import our component
import TodoList from './components/TodoList'
import CreateTodo from './components/CreateTodo'

export default {
  name: 'app',
  // reference to the TodoList component in the compoents property
  // reference to the CreateTodo component in the compoents property
  components: {
    TodoList,
    CreateTodo
  },
  // data function avails data to the template
  // TodoList data have three properties, title, project, done
  data () {
    return {
      todos: [{
        title: 'Todo A',
        project: 'Project A',
        done: false
      }, {
        title: 'Todo B',
        project: 'Project B',
        done: true
      }, {
        title: 'Todo C',
        project: 'Project C',
        done: false
      }, {
        title: 'Todo D',
        project: 'Project D',
        done: false
      }]
    }
  },
  methods: {
    createTodo (newTodo) {
      this.todos.push(newTodo)
    }
  }
}
</script>

// Style Section
// Improve the appearance of the template within the component
<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
