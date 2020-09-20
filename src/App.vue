<template>
  <div id="app">
    <h1>
      {{title}}
    </h1>
    <input 
      type="text"
      class="nes-input"
      placeholder="Add todo..."
      v-on:keyup.enter="addTodo"> 
    <TodoList
     v-bind:todos="todos"
     v-on:remove-todo="removeTodo" />
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'

export default {
  name: 'App',
  components: {
    TodoList
  },
  methods: {
    addTodo(event){
      const text = event.target.value;
      if(text.trim().length>0){

      this.todos.push({
        id: Date.now(),
        text,
        completed: false
      });
      event.target.value = '';
      }
    },
    removeTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    }
  },
  data() {
    return {
      title: 'TODOS',
      todos: [
        {
          id: Date.now(),
          text: 'Test',
          completed: false
        },
      ],
    }
  }
}
</script>

<style>
html, body, pre, code, kbd, samp {
  font-family: "Press Start 2P";
}

body {
  background: #20262E;
  padding: 20px;
}

#app {
  background: #fff;
  border-radius: 4px;
  padding: 20px;
  transition: all 0.2s;
}
</style>