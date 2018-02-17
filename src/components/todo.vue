<template lang="pug">
  .todo
    todo-input(
      @addTodo="addNewTodo"
    )
    todo-list(
      :todos="todos"
    )
</template>

<script>
import todoInput from "./todoInput";
import todoList from "./todoList";

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
    todoInput,
    todoList
  }  
}
</script>


<style lang="scss" src="styles/todo.scss"></style>

