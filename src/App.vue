<template>
  <div id="app">
    <h1>Todo List</h1>
    <todo-input @add-todo="addTodo"></todo-input>
    <todo-list
      :todos="todos"
      @delete-todo="deleteTodo"
      @edit-todo="editTodo"
      @close-edit="closeEdit"
    ></todo-list>
  </div>
</template>

<script>
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
      this.todos.push({ text: todo, completed: false, isEditing: false })
    },
    deleteTodo(index) {
      this.todos.splice(index, 1)
    },
    editTodo({ index, newText }) {
      this.todos[index].text = newText
      // this.todos[index].isEditing = false
    }
  }
}
</script>

<style scoped>
/* 스타일 부분은 그대로 유지 */
</style>
