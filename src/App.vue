<template>
  <div id="app">
    <!-- <nav>
      <a href="#page-1">1</a>
      <a href="#page-2">2</a>
      <a href="#page-3">3</a>
    </nav> -->
    <div id="h1">Todo List</div>
    <todo-input @add-todo="addTodo"></todo-input>
    <todo-list
      :todos="todos"
      @delete-todo="deleteTodo"
      @edit-todo="editTodo"
      @close-edit="closeEdit"
    />
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
