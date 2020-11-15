<template>
  <div id="app" v-bind:title="message" v-if="seen">
    Hover your mouse over me for a few seconds to see my dynamically bound
    title!

    <br />
    {{ message }}
    <br />
    <input v-model="message" />
    <br />
    <ol v-on:click="addTodo">
        <todo-item v-for="todo in todos" v-bind:todo="todo" v-bind:key="todo.id"/>
    </ol>
  </div>
</template>

<script>
import TodoItem from './components/TodoItem.vue';
export default {
  components: { TodoItem },
  name: "App",
  data: () => ({
    message: "You loaded this page on " + new Date().toLocaleString(),
    seen: 1,
    todos: [{id:1,  text: "Todo1" }, {id:2, text: "Todo2" }, {id:3, text: "Todo3" }],
  }),
  methods: {
    addTodo: function (e) {
      e.preventDefault();
      console.log(this, e.preventDefault, e);
      this.todos.push({ text: "todo xxx" });
    },
  },
};
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
</style>
