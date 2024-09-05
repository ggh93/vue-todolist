<template>
  <ul>
    <li v-for="(todo, index) in todos" :key="index">
      <input type="checkbox" v-model="todo.completed" />
      <span
        v-if="!todo.isEditing"
        :style="{ textDecoration: todo.completed ? 'line-through' : 'none' }"
      >
        {{ todo.text }}
      </span>

      <input v-else v-model="newText" @keyup.enter="submitEdit(todo, index)" />

      <!-- 수정 버튼 (수정 모드가 아닐 때만 표시) -->
      <button v-if="!todo.isEditing" @click="startEdit(todo, index)">Edit</button>

      <button @click="$emit('delete-todo', index)">Delete</button>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    todos: Array
  },
  data() {
    return {
      newText: '' // 수정된 텍스트를 임시로 저장
    }
  },
  methods: {
    startEdit(todo, index) {
      this.newText = this.todos[index].text
      this.todos.forEach((todo, i) => {
        if (i !== index) {
          todo.isEditing = false
        }
      })
      // 선택한 항목만 수정 모드로 전환
      this.newText = this.todos[index].text
      // 모든 항목의 isEditing 상태를 false로 변경
      todo.isEditing = true
    },
    submitEdit(todo, index) {
      todo.text = this.newText
      todo.isEditing = false
      if (this.newText.trim() !== '') {
        this.$emit('edit-todo', { index, newText: this.newText }) // 부모에게 수정 이벤트 전달
        this.newText = '' // 수정후 입력필드 초기화
      }
    }
  }
}
</script>
