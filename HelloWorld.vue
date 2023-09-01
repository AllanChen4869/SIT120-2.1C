<template>
  <div id="Todo">
    <h1>Todo App</h1>
    <div class="todo-container">
      <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Add a new task">
      <ul class="todo-list">
        <li v-for="(todo, index) in todos" :key="index">
          <input type="checkbox" v-model="todo.completed">
          <span :class="{ completed: todo.completed }">{{ todo.text }}</span>
          <button @click="deleteTodo(index)">Delete</button>
        </li>
      </ul>
    </div>
  </div>
</template>


<script>
export default {
  data() {
    return {
      newTodo: "",
      todos: [],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() === "") return;
      this.todos.push({ text: this.newTodo, completed: false });
      this.newTodo = "";
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  input[type="text"] {
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 70%;
  height: 40;
  font-size: 20px;
  }

  #app {
    font-family: Arial, sans-serif;
    text-align: center;
  }

  .todo-container {
    max-width: 400px;
    margin: 0 auto;
  }

  .todo-list {
    list-style-type: none;
    padding: 0;
  }

  .todo-list li {
    display: flex;
    align-items: center;
    margin: 10px 0;
  }

  input[type="checkbox"] {
    margin-right: 10px;
  }

  .completed {
    text-decoration: line-through;
    color: #888;
  }

  button {
    padding: 5px 10px;
    margin-left: 10px;
    background-color: #6cd14d;
    border: line;
    color: white;
    cursor: pointer;
  }
</style>
