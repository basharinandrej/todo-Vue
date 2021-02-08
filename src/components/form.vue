<template>
  <form class="form" v-on:submit.prevent="submitHandler">
    <input type="text" v-model="title">
    <button type="submit">Send</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: ''
    }
  },
  methods: {
    submitHandler() {
      if(this.title.trim()) {
        let newTodo = {
          id: Date.now(),
          title: this.title,
          complete: false
        }
        this.$emit('add-todo', newTodo)
        this.title = ''
      }
    }
  }
}
</script>

<style scoped>
.form {
  margin-bottom: 24px;
}
</style>