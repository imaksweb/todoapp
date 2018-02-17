<template lang="pug">
  .todo-list
    .content
      ul.list
        li.item(
          v-for="todo in todos"
        ) {{todo.name}}
    .footer
      .footer-content
        .counter Кол-во заданий: 0
      .filter
        button(type="button") All
        button(type="button") Active
        button(type="button") Completed
</template>

<script>
export default {
  props: {
    todos: Array
  }
}
</script>


<style lang="scss" src="styles/todoList.scss"></style>

