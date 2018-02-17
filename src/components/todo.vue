<template lang="pug">
  .todo
    todo-input(
      @addTodo="addNewTodo"
    )
</template>

<script>
import todoInput from "./todoInput";

export default {
  data() {
    return {
      todos: []
    }
  },
  methods: {
    addNewTodo(todo) {
      this.todos.push(todo);
    }
  },
  components: {
    todoInput
  }  
}
</script>


<style lang="scss" src="styles/todo.scss"></style>

