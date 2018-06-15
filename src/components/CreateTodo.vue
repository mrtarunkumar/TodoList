// CreateTodo component

// Template Section
// Visual part of the component
<template>
<div class='ui basic content center aligned segment'>
    <button class='ui basic button icon' v-on:click="openForm" v-show="!isCreating">
      <i class='plus icon'></i>
    </button>
    <div class='ui centered card' v-show="isCreating">
      <div class='content'>
        <div class='ui form'>
          <div class='field'>
            <label>Title</label>
            <input v-model="titleText" type='text' ref='title' defaultValue="">
          </div>
          <div class='field'>
            <label>Project</label>
            <input v-model="projectText" type='text' ref='project' defaultValue="">
          </div>
          <div class='ui two button attached buttons'>
            <!-- Event handler on the create button -->
            <!-- This will trigger the sendForm method -->
            <button class='ui basic blue button' v-on:click="sendForm()">
              Create
            </button>
            <!-- Event handler on the cancel button -->
            <!-- This will trigger the closeForm method -->
            <button class='ui basic red button' v-on:click="closeForm">
              Cancel
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

// Component Class Section
// Behaviour, events, data storage part of the component
<script type = "text/javascript" >
export default {
  // CreateTodo data have three properties, titleText, projectText, isCreating
  data () {
    return {
      titleText: '',
      projectText: '',
      isCreating: false
    }
  },
  methods: {
    openForm () {
      this.isCreating = true
    },
    closeForm () {
      this.isCreating = false
    },
    sendForm () {
      if (this.titleText.length > 0 && this.projectText.length > 0) {
        const title = this.titleText
        const project = this.projectText
        this.$emit('create-todo', {
          title,
          project,
          done: false
        })
        this.titleText = ''
        this.projectText = ''
        this.isCreating = false
      }
    }
  }
}
</script>

// Style Section
// Improve the appearance of the template within the component
<style>
</style>
