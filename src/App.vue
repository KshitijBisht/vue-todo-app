<template>
  <div id="app">
    <section class="todoapp">
      <header class="header">
        <h1 class="title">todos</h1>
        <input
          class="new-todo"
          placeholder="What needs to be done?"
          v-model="newTodo"
          @keyup.enter="addTodo"
        >
      </header>
      <section class="main">
        <ul class="todo-list">
          <li class="todo" v-for="(todo, key) in todos" :key="key">
            <div class="view">
              <input type="checkbox" @click="check(todo)">
              <label>{{ todo.text }}</label>
              <button v-show="todo.done" class="destroy" @click="removeTodo(todos.indexOf(todo))">X</button>
              <br/>
            </div>
          </li>
        </ul>
      </section>
    </section>
  </div>
</template>
<script>
export default {
  name: "App",
  data() {
    return {
      todos: [
        
      ],
      newTodo: ""
    };
  },
  methods: {
    addTodo(event) {
      const text = event.target.value;
      this.todos.push({text:text,done:false});
      event.target.value = ""

     
    },
    removeTodo(i) {
      return this.todos.splice(i,1);
    },

    check(todo){
      todo.done = !todo.done
      
    }
  }
};
</script>



<style lang="css" src="./style.css">
</style>
