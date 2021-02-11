<template>
  <div id="app">
    <Todos v-bind:todos = "todos" v-on:del-todo = "deleteTodo"/>
    <AddTodo v-on:add-todo="onAddTodo"/>
  </div>
</template>

<script>
  import Todos from './components/Todos';
  import AddTodo from './components/AddTodo';

  export default {
    name: 'App',
    components: {
      Todos,
      AddTodo
    },
    data() {
      return {
        todos: [
          {
            id: 1,
            title: 'food the cat',
            completed: true
          },
                  {
            id: 2,
            title: 'food fishes',
            completed: false
          },
                  {
            id: 3,
            title: 'food the dog',
            completed: false
          }
        ]
      }
    },
    methods: {
      deleteTodo(id) {
        this.todos = this.todos.filter(todo => todo.id !== id)
      },
      onAddTodo(newTodo) {
        this.todos = [...this.todos, newTodo];
      }
    }
  }
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  html {
    font-size: 10px;
  }
  
  body {
    display: flex;
    flex-direction: row;
    justify-content: center;
    font-family: Arial, sans-serif;
    color: #2c3e50;
    font-size: 1.6rem;
    margin-top: 60px;
    position: relative;
  }
</style>
