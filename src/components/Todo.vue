<template>
  <li
    class="flex border border-gray-400 shadow-lg m-3 rounded-tl-lg rounded-br-lg p-0 overflow-hidden bg-gray-200 eachitem"
  >
    <div class="flex justify-start flex-3 mr-4 p-2 border-r">
      <img v-bind:src="todo.image" v-bind:alt="todo.name" class="p-2 rounded-full" />
    </div>
    <div class="flex flex-col flex-1 mr-4 p-2">
      <div class="text-gray-800 flex-1 flex-wrap">
        <span class="font-normal text-sm">Name :</span>
        <input
          type="text"
          class="font-bold text-2xl bg-gray-200 focus:bg-white"
          v-model="todo.name"
          :disabled="!todo.editing"
        />
      </div>
      <div class="text-gray-700 flex-1 flex-wrap">
        <span class="font-normal text-sm">Status :</span>
        <select v-model="todo.status" class="font-bold text-lg bg-white border p-1" v-if="todo.editing">
          <option disabled value>Please select one</option>
          <option value="Running">Running</option>
          <option value="Coming Soon">Coming Soon</option>
          <option value="Closed">Closed</option>
        </select>
        <span class="font-bold text-xl bg-gray-200" v-else>{{todo.status}}</span>
      </div>
    </div>
    <div class="flex flex-col flex-3 justify-center border-l">
      <button
        v-if="todo.editing"
        class="w-full h-full bg-green-200 pl-5 pr-5 text-gray-800 hover:text-gray-900 hover:bg-green-400"
        v-on:click="saveTodo"
      >
        <font-awesome-icon icon="check" />
        <span>Save</span>
      </button>
      <button
        v-else
        class="w-full h-full bg-yellow-200 pl-5 pr-5 text-gray-800 hover:text-gray-900 hover:bg-yellow-400"
        v-on:click="editTodo"
      >
        <font-awesome-icon icon="edit" />
        <span>Edit</span>
      </button>
      <button
        class="w-full h-full bg-red-200 pl-5 pr-5 text-gray-800 hover:text-gray-900 hover:bg-red-400"
        v-on:click="deleteTodoItem"
      >
        <font-awesome-icon icon="trash-alt" />
        <span>Delete</span>
      </button>
    </div>
  </li>
</template>

<script>
export default {
  name: 'todo',
  props: ['todo', 'updateTodo', 'deleteTodo'],
  methods: {
    editTodo () {
      this.todo.editing = !this.todo.editing
    },
    saveTodo () {
      this.updateTodo(this.todo)
    },
    deleteTodoItem () {
      this.deleteTodo(this.todo.id)
    }
  }
}
</script>
