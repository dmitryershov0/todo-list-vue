<template>
	<li class="flex">
		<label>
        <input type="checkbox"
			class="nes-checkbox"
			v-model="todo.completed">
        <span></span>
      </label>
		<del v-if="todo.completed">
			{{ todo.text }}
		</del>
      <span v-else>{{ todo.text }}</span>
      <div class="space"></div>
		<button class="nes-btn is-error padding"
			v-on:click="remove(todo.id)">
			X
		</button>
    </li>
</template>

<script>
export default {
  name: 'TodoItem',
  props: [
    "todo"
  ],
  methods: {
		remove(id)
		{
			this.$emit('remove-todo', id)
		}
  }
}
</script>

<style scoped>
li {
  margin: 8px 0;
}

del {
  color: rgba(0, 0, 0, 0.3);
}

.padding {
  padding: 1px 7px 2px;
}

.flex {
  display: flex;
}

.space {
  flex-grow: 1;
}
</style>
