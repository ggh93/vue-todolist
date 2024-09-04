<template>
  <ul>
    <li v-for="(todo, index) in todos" :key="index">
      {{ todo }}
      <button @click="$emit('delete-todo', index)">Delete</button>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    todos: Array
  }
}
</script>

<style scoped>
/* 스타일 추가 */
</style>
