// Todo component

// Template Section
// Visual part of the component
<template>
<div class="mbs">
  <div class='ui centered card'>
    <div class='content' v-show="!isEditing">
      <div class='header'>
          {{ todo.title }}
        </div>
        <div class='meta'>
          {{ todo.project }}
        </div>
        <div class='extra content'>
          <!-- Event handler on the edit span-->
          <!-- This will trigger the showForm method -->
          <span class='right floated edit icon' v-on:click="showForm">
            <i class='edit icon'></i>
          </span>
          <!-- Event handler on the delete span-->
          <!-- This will trigger the deleteTodo method -->
          <span class='right floated trash icon' v-on:click="deleteTodo(todo)">
              <i class="trash icon"></i>
          </span>
        </div>
    </div>
    <!-- show form when we are in edit mode -->
    <div class="content" v-show="isEditing">
      <div class='ui form'>
        <div class='field'>
          <label>Title</label>
          <!-- Bound the form values to the todo values -->
          <!-- Can edit and update the values -->
          <input type='text' v-model="todo.title" >
        </div>
        <div class='field'>
          <label>Project</label>
          <input type='text' v-model="todo.project" >
        </div>
        <div class='ui two button attached buttons'>
          <!-- Event handler on the close button -->
          <!-- This will trigger the hideForm method -->
          <button class='ui basic blue button' v-on:click="hideForm">
            Close X
          </button>
        </div>
      </div>
    </div>

      <div class='ui bottom attached green basic button' v-show="!isEditing && todo.done">
        Completed
      </div>
      <div class='ui bottom attached red basic button' v-show="!isEditing &&  !todo.done">
        Pending
      </div>
  </div>
</div>
</template>

// Component Class Section
// Behaviour, events, data storage part of the component
<script type = "text/javascript" >
export default {
  props: ['todo'],
  // Todo data properties: isEditing
  // This is used to determine whether the
  // Todo application is in edit mode
  data () {
    return {
      isEditing: false
    }
  },
  methods: {
    showForm () {
      this.isEditing = true
    },
    hideForm () {
      this.isEditing = false
    },
    deleteTodo (todo) {
      this.$emit('delete-todo', todo)
    }
  }
}
</script>

// Style Section
// Improve the appearance of the template within the component
<style>
.mbs {
  margin-bottom: 10px;
}
</style>
