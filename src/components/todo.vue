<template lang="pug">
  .todo
    todo-input(
      @addTodo="addNewTodo"
    )
    todo-list(
      :todos="todos"
      :todoLeft="todoLeft"
      @checkTodo="checkTodo"
      @removeTodo="removeTodo"
    )
</template>

<script>
import todoInput from "./todoInput";
import todoList from "./todoList";

export default {
  data() {
    return {
      todos: [],
      todoLeft: 0
    }
  },
  methods: {
    addNewTodo(todo) {
      this.todos.push(todo);
      this.todoLeft = this.todos.length
    },
    checkTodo(todo) {
      this.todos = this.todos.map(item => item.id === todo.id ? todo : item)
    },
    removeTodo(todoID) {
      this.todos = this.todos.filter(item => item.id !== todoID)
      this.todoLeft = this.todos.length
    }
  },
  components: {
    todoInput,
    todoList
  }  
}
</script>


<style lang="scss" src="styles/todo.scss"></style>

