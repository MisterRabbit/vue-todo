<template>
  <div class="todo">
    <ul>
      <TodoItem
        v-for="(todo, i) in todos"
        :index="i"
        :todo="todo"
        :key="todo.id"
        v-on:remove-todo="removeTodo"
      />
    </ul>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem'
export default {
  props: ['todos'],
  components: {
    TodoItem
  },
  methods: {
    removeTodo(id) {
      this.$emit('remove-todo', id)
    }
  }
}
</script>

<style scoped>
  .todo {
    max-width: 500px;
    margin: 3rem auto;
  }
  ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }
</style>