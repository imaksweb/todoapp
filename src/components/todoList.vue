<template lang="pug">
  .todo-list(v-if="todos.length")
    .content
      ul.list
        li.item(
          v-for="todo in filteredItems"
        )
          todo-item(
            :todo="todo"
            @checkTodo="checkTodo"
            @removeTodo="removeTodo"
          )
    .footer
      .footer-content
        .counter Заданий осталось: {{todoLeft}}
      .filter
        button(type="button" @click="applyFilter('all')" :class="{active: filter === 'all'}") All
        button(type="button" @click="applyFilter('active')" :class="{active: filter === 'active'}") Active
        button(type="button" @click="applyFilter('completed')" :class="{active: filter === 'completed'}") Completed
</template>

<script>
import todoItem from "./todoItem";

export default {
  props: {
    todos: Array,
    todoLeft: Number
  },
  data() {
    return {
      filter: 'all'
    }
  },
  computed: {
    filteredItems() {
      switch(this.filter) {
        case 'all':
          return this.todos
        case 'active':
          return this.todos.filter(item => !item.checked)
        case 'completed':
          return this.todos.filter(item => item.checked)
      }
    }
  },
  methods: {
    checkTodo(todo) {
      this.$emit('checkTodo', todo)
    },
    removeTodo(todoID) {
      this.$emit('removeTodo', todoID)
    },
    applyFilter(filterName) {
      this.filter = filterName
    }
  },
  components: {
    todoItem
  }
}
</script>


<style lang="scss" src="styles/todoList.scss"></style>

