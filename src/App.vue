<template>
  <div id="app" class="container mx-auto">
    <div class="flex flex-col max-w-7xl mx-auto">
      <main-title v-bind:title="main_title"></main-title>
      <status-bar v-bind:todoList="todo_list"></status-bar>
      <todo-table :addTodo="addTodo">
        <todo-list v-bind:todoList="todo_list" :updateTodo="updateTodo" :deleteTodo="deleteTodo"></todo-list>
      </todo-table>
    </div>
  </div>
</template>

<script>
import TodoList from './components/TodoList'
import MainTitle from './components/MainTitle'
import StatusBar from './components/StatusBar'
import TodoTable from './components/TodoTable'
export default {
  name: 'App',
  components: {
    MainTitle,
    TodoList,
    TodoTable,
    StatusBar
  },
  data () {
    return {
      main_title: 'Popular Movie List',
      todo_list: [
        {
          id: 1,
          name: 'Movie 1',
          status: 'Running',
          editing: false,
          deleted: false,
          image: 'https://picsum.photos/60/60'
        },
        {
          id: 2,
          name: 'Movie 2',
          status: 'Coming Soon',
          editing: false,
          deleted: false,
          image: 'https://picsum.photos/60/60'
        },
        {
          id: 3,
          name: 'Movie 3',
          status: 'Running',
          editing: false,
          deleted: false,
          image: 'https://picsum.photos/60/60'
        },
        {
          id: 4,
          name: 'Movie 4',
          status: 'Closed',
          editing: false,
          deleted: false,
          image: 'https://picsum.photos/60/60'
        },
        {
          id: 5,
          name: 'Movie 5',
          status: 'Coming Soon',
          editing: false,
          deleted: false,
          image: 'https://picsum.photos/60/60'
        }
      ]
    }
  },
  methods: {
    addTodo () {
      if (isEditing(this.todo_list)) {
        alert('Cannot add movie while editing another')
      } else {
        const newTodo = {
          id: getNextId(this.todo_list),
          name: '',
          status: '',
          editing: true,
          deleted: false,
          image: 'https://picsum.photos/60/60'
        }
        this.todo_list = [...this.todo_list, newTodo]
      }
    },
    updateTodo (todo) {
      this.todo_list = this.todo_list.map(todoItem => {
        if (todoItem.id === todo.id) {
          return { ...todoItem, ...todo, editing: false }
        } else {
          return todoItem
        }
      })
    },
    deleteTodo (todoId) {
      this.todo_list = this.todo_list
        .map(todoItem => {
          if (todoItem.id === todoId) {
            return { ...todoItem, deleted: true }
          } else {
            return todoItem
          }
        })
        .filter(todoItem => !todoItem.deleted)
    }
  }
}

function isEditing (todoList) {
  return todoList.some(todo => todo.editing)
}

function getNextId (todoList) {
  const latestId = todoList.reduce((high, curr) => {
    if (curr.id > high) {
      return curr.id
    } else {
      return high
    }
  }, 0)
  return latestId + 1
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
</style>
