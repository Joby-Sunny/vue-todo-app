<template>
  <div class="flex flex-col mt-5 border-t border-gray-300 pt-5">
    <div class="flex justify-between pb-2 pt-2">
      <h3 class="text-bold text-gray-700 font-medium text-3xl">Movie Table</h3>
      <button
        class="bg-green-200 hover:bg-green-400 text-green-600 hover:text-white overflow-hidden rounded pl-3 pr-3"
        v-on:click="addTodo"
      >
        <font-awesome-icon icon="plus" />
        <span>Add Movie</span>
      </button>
    </div>
    <div class="p-0 m-0 border-gray-300 border rounded overflow-hidden">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TodoTable',
  props: ['addTodo']
}
</script>
