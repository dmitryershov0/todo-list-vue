<template>
  <ul>
      <TodoItem
      :key="todo.id"
      v-for="todo in todos"
      v-bind:todo="todo"
      v-on:remove-todo="removeTodo" />
    
  </ul>
</template>

<script>
import TodoItem from './TodoItem.vue'

export default {
  name: 'TodoList',
  components: {
    TodoItem
  },
   props: [
    "todos"
  ],
  methods:{
    removeTodo(id) {
      this.$emit('remove-todo', id);
    }
  } 
}
</script>

<style scoped>
</style>
