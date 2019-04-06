<template>
  <div>
    <div class="ui segment"><div class="ui center aligned header">To-Do List</div></div>
    <p class="tasks">Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p class="tasks">Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    <todo v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-for="todo in todos" :todo.sync="todo"></todo>

  </div>
</template>

<script type = "text/javascript" >
  import Todo from './Todo';

  export default {
    props: ['todos'],
    components: {
      Todo,
    },
    methods: {
      deleteTodo(todo) {
      console.log(this.todos.indexOf(todo));
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },
    completeTodo(todo) {
      console.log("todolist");
      console.log(this.todos.indexOf(todo));
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = true;
    },
  },
  };
</script>
<style>
  p.tasks{
    text-align: center;
  }
</style>
