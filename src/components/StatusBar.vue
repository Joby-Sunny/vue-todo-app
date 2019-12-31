<template>
  <div
    class="flex flex-row justify-around w-full border border-gray-400 rounded p-0 text-base text-center text-gray-600 overflow-hidden"
  >
    <div class="font-light w-full h-full p-5 m-0 bg-green-200 text-green-700">
      <span>
        <font-awesome-icon icon="play" />
      </span>
      <span>Currently Running:</span>
      <span class>{{todoList.filter(todo => todo.status === 'Running').length}}</span>
    </div>
    <div class="font-light w-full h-full p-5 m-0 bg-yellow-200 text-yellow-700">
      <span>
        <font-awesome-icon icon="pause" />
      </span>
      <span>Coming Soon:</span>
      <span>{{todoList.filter(todo => todo.status === 'Coming Soon').length}}</span>
    </div>
    <div class="font-light w-full h-full p-5 m-0 bg-red-200 text-red-700">
      <span>
        <font-awesome-icon icon="stop" />
      </span>
      <span>Closed:</span>
      <span>{{todoList.filter(todo => todo.status === 'Closed').length}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'statusbar',
  props: ['todoList']
}
</script>
