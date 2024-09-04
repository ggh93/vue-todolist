<template>
  <div id="app">
    <h1>Todo List</h1>
    <TodoInputVue @add-todo="addTodo" />
    <TodoListVue :todos="todos" @delete-todo="deleteDoto" />
    <!-- <todo-input @add-todo="addTodo"></todo-input>
    <todo-list :todos="todos" @delete-todo="deleteDoto"></todo-list> -->
  </div>
</template>

<script>
import TodoInput from './components/TodoInpu'
import TodoList from './components/TodoList.vue'

export default {
  components: {
    TodoInputVue,
    TodoListVue
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
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
