<template>
  <ul class="flex flex-wrap flex-auto w-full">
    <Todo
      v-for="todo in todoList"
      :todo="todo"
      :key="todo.id"
      :updateTodo="updateTodo"
      :deleteTodo="deleteTodo"
    ></Todo>
  </ul>
</template>

<style scoped>
.eachitem {
  min-width: 615px;
}
</style>

<script>
import Todo from './Todo'
export default {
  name: 'todo-list',
  props: ['todoList', 'updateTodo', 'deleteTodo'],
  components: {
    Todo
  }
}
</script>
