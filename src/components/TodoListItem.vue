<template>
  <li class="main-list__item">
    <span v-bind:class="{done: todo.complete}">
      <input type="checkbox" v-on:change="clickHandler">
      <strong>{{ idx + 1 }}</strong>
      {{ todo.title }}
    </span>
    <button @click="$emit('remove-todo', todo.id)">&times;</button>
  </li>
</template>
<script>
export default {
  name: 'todoItem',
  props: ['todo', 'idx'],
  methods: {
    clickHandler() {
      this.todo.complete = !this.todo.complete
    }
  }
}
</script>

<style>
.main-list__item {
  display: flex;
  list-style: none;
  width: 400px;
  margin-bottom: 4px;
}
.main-list__item input {
  margin-right: 32px;
}
.main-list__item button {
  margin-left: auto;
}
.main-list__item .done {
  text-decoration: line-through;
}
</style>