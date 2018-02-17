<template lang="pug">
  .todo-input
    input(
      type="text"
      @keydown.enter="addTodo"
      v-model="todo.name"
    ).input
</template>

<script>
export default {
  data() {
    return {
      todo: {
        id: 0,
        name: '',
        checked: false
      }
    }
  },
  methods: {
    addTodo(e) {
      this.$emit('addTodo', {...this.todo});
      this.todo.name = '';
    }
  }
}
</script>


<style lang="scss" src="styles/todoInput.scss"></style>

