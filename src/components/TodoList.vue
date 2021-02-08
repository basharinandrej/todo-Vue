<template>
  <ul class="main-list">
    <TodoItem
      v-for="(todo, idx) of todos"
      v-bind:todo="todo"
      v-bind:idx="idx"
      v-on:remove-todo="removeTodoHandler"
    />
  </ul>
</template>

<script>
import TodoItem from './TodoListItem.vue'
export default {
  name: 'TodoList',
  props: ['todos'],
  components: {
    TodoItem
  },
  methods: {
    removeTodoHandler(id) {
      this.$emit('remove-todo', id)
    }
  }
}
</script>

<style>
.main-list{
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  padding-left: 0;
}
</style>