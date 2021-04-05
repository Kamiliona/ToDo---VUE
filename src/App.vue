<template>
  <div id="app">
    <h1>Kamil & Pete's ToDo's</h1>
    <form v-on:submit.prevent="saveNewTodo">
      <label for="new-todo">Add new todo </label>
      <input type="text" id="new-todo" v-model="newTodo.name">
      <input type="radio" v-model="newTodo.isPriority" v-bind:value="false">low
      <input type="radio" v-model="newTodo.isPriority" v-bind:value="true">high
      <input type="submit" value="save">
    </form> 
    <ul>
      <li v-for="todo, index in todos" v-bind:key="index">
        <span v-bind:class="todo.isPriority ? 'priority' : 'not-priority'">{{todo.name}}</span>
        <span v-if="todo.isPriority"> </span>
      </li>
    </ul>
  </div>
</template>

<script>

export default {

  name: 'App',
  data() {
    return {
    todos: [
      {name:"Buy shopping", isPriority: false},
      {name:"Clean bathroom", isPriority: true}, 
      {name:"Car's MOT", isPriority: false},
      {name:"Make a soup", isPriority: true},
      {name:"Have a bath", isPriority: true}

    ],
    newTodo: {
      name:"",
      isPriority: null
    }
    }
},
methods: {
  saveNewTodo: function() {
    if (this.newTodo === "") {
      return
    }
    this.todos.push(this.newTodo);
    this.newTodo= {
      name:"",
      isPriority: null
    }
  }
}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

ul {
  list-style-type: none; /* Remove bullets */
  padding: 40px; /* Remove padding */
  margin: 0; /* Remove margins */
  
}

li {
  
  border:1px solid #000;
  padding:20px;
  width: 30%;
  margin-left: auto;
  margin-right: auto;
  
}

.priority {
  color: goldenrod;
  font-weight:bolder;

}
</style>
