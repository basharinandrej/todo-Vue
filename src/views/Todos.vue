<template>
  <div>
    <h2>Todo</h2>
    <Form
        @add-todo="addTodo"
    />
    <TodoList
        v-bind:todos="todos"
        v-on:remove-todo="removeTodoHandler"
    />
    <router-link to="/">
      Home
    </router-link>
  </div>
</template>

<script>
import TodoList from '../components/TodoList.vue'
import Form from '../components/form.vue'

export default {
  name: 'App',
  data() {
    return {
      todos: []
    }
  },
  methods: {
    removeTodoHandler(id) {
      this.todos = this.todos.filter(t => t.id !== id)
    },
    addTodo(todo) {
      this.todos.push(todo)
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=4')
        .then(response => response.json())
        .then(json => this.todos = json)
  },
  components: {
    TodoList, Form
  }
}
</script>