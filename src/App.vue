<template>
  <div id="app">
    <todo-header></todo-header>
    <todo-input v-on:addItem="addTodoItem"></todo-input>
    <todo-list v-bind:items="todoItems" v-on:removeItem="removeTodoItem"></todo-list>
    <todo-footer v-on:clear="clearTodoItems"></todo-footer>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  name: 'app',
  components: {
    TodoHeader,
    TodoInput,
    TodoList,
    TodoFooter
  },
  data() {
    return {
      todoItems: []
    }
  },
  methods: {
    addTodoItem: function(value){
      this.todoItems.push(value);
      localStorage.setItem(value, value);
    },
    fetchTodoItems: function () {
      for (var i = 0; i < localStorage.length; i++) {
        var key = localStorage.key(i);
        // if (key === "randid" || key === "loglevel:webpack-dev-server")
        //   continue;
        if (key !== "randid" && key !== "loglevel:webpack-dev-server") {
          var item = localStorage.getItem(key);
          this.todoItems.push(item);
        }
      }
    },
    clearTodoItems: function () {
      this.todoItems = [];
      localStorage.clear();
    },
    removeTodoItem: function (todoItem, index) {
      this.todoItems.splice(index, 1);
      localStorage.removeItem(todoItem);
    }
  },
  created() {
    this.fetchTodoItems();
  }
}

</script>

<style>
</style>
