<template>
  <li>
    <span v-bind:class="{done: todo.completed}">
      <input type="checkbox" v-on:change="todo.completed = !todo.completed">
      <b>{{index + 1}}.</b> {{todo.title | uppercase}}
    </span>
    <button class="remove" v-on:click="$emit('remove-todo', todo.id)">&times;</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    },
    index: Number
  },
  filters: {
    uppercase(value) {
      return value.toUpperCase()
    }
  }
}
</script>

<style scoped>
  li {
    border: 1px;
    display: flex;
    justify-content: space-between;
    padding: .5rem 2rem;
    margin-bottom: 1rem;
  }
  input {
    margin-right: 2rem;
    cursor: pointer;
  }
  .remove {
    background: rgb(170, 2, 2);
    color: #fff;
    border-radius: 50%;
    border: none;
    font-weight: bold;
    cursor: pointer;
  }
  .done {
    text-decoration: line-through;
  }
</style>