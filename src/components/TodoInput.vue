<template>
  <div>
    <input v-model="newTodo" placeholder="Add a new todo" @keyup.enter="submitTodo" />
    <button @click="submitTodo">Add</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: ''
    }
  },
  methods: {
    submitTodo() {
      if (tihs.newTodo.trim() !== '') {
        this.$emit('add-todo', this.newTodo)
        this.newTodo = ''
      }
    }
  }
}
</script>

<style lang="scss"></style