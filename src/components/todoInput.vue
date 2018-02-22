<template lang="pug">
  .todo-input
    input(
      type="text"
      @keydown.enter="addTodo"
      v-model="todo.name"
    ).input
</template>

<script>
let uniqueId = 1;
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
      this.todo.id = uniqueId++;
      this.$emit('addTodo', {...this.todo});
      this.todo.name = '';
    }
  }
}
</script>


<style lang="scss" src="styles/todoInput.scss"></style>

