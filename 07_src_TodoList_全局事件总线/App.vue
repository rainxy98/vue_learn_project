<template>
  <div id="app">
    <TaskHeader :addTask="addTask"/>
    <TaskList :todos="todos"/>
    <TaskFooter v-if="this.todos.length" :todos="todos"/>
  </div>
</template>

<script>
import TaskHeader from './components/TaskHeader'
import TaskFooter from './components/TaskFooter'
import TaskList from './components/TaskList'

export default {
  name: 'App',
  components: {
    TaskHeader,
    TaskFooter,
    TaskList
  },
  data() {
    return {
     todos: JSON.parse(localStorage.getItem('todos')) || []
    }
  },
  watch: {
    todos: {
      deep: true,
      handler(val) {
        localStorage.setItem('todos', JSON.stringify(this.todos));
      }
    }
  },
  methods: {
    addTask(todo) {
      this.todos.unshift(todo);
    },
    checkChange(id) {
      this.todos.forEach((todo) => {
        if (todo.id === id) todo.done = !todo.done;
      });
    },
    checkAll(check) {
      this.todos.forEach(todo => todo.done = check);
    },
    deleteItemById(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    clearTask() {
      this.todos = this.todos.filter(todo => !todo.done);
    }
  },
  mounted() {
    this.$bus.$on('checkChange', this.checkChange);
    this.$bus.$on('deleteItemById', this.deleteItemById);
    this.$bus.$on('checkAll', this.checkAll);
    this.$bus.$on('clearTask', this.clearTask);
  },
  beforeDestroy() {
    this.$bus.$off('checkChange');
    this.$bus.$off('deleteItemById');
    this.$bus.$off('checkAll');
    this.$bus.$off('clearTask');
  }
}
</script>

<style>

</style>
