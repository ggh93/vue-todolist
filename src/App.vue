<template>
  <div id="app">
    <h1>Todo List</h1>
    <todo-input @add-todo="addTodo"></todo-input>
    <todo-list :todos="todos" @delete-todo="deleteTodo"></todo-list>
  </div>
</template>

<script>
// 주석 제거 및 올바른 경로 확인
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'

export default {
  components: {
    TodoInput,
    TodoList
  },
  data() {
    return {
      todos: []
    }
  },
  methods: {
    addTodo(todo) {
      this.todos.push(todo)
    },
    deleteTodo(index) {
      this.todos.splice(index, 1)
    }
  }
}
</script>

<style scoped>
/* 스타일 부분은 그대로 유지 */
</style>
