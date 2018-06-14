// TodoList component

// Template Section
// Visual part of the component
<template>
<div>
  <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
  <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
  // Loop through using v-for="item in items" syntax
  <div class='ui centered card' v-bind:key="todo.title" v-for="todo in todos">
    <div class='content'>
      <div class='header'>
          {{ todo.title }}
        </div>
        <div class='meta'>
          {{ todo.project }}
        </div>
        <div class='extra content'>
          <span class='right floated edit icon'>
            <i class='edit icon'></i>
          </span>
        </div>
    </div>

      <div class='ui bottom attached green basic button' v-show="todo.done">
        Completed
      </div>
      <div class='ui bottom attached red basic button' v-show="!todo.done">
        Complete
      </div>
  </div>
</div>
</template>

// Component Class Section
// Behaviour, events, data storage part of the component
<script type = "text/javascript" >
export default {
  props: ['todos']
}
</script>

// Style Section
// Improve the appearance of the template within the component
<style>
</style>
