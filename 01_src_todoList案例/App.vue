<template>
  <div id="app">
    <TaskHeader :addTask="addTask"/>
    <TaskList :todos="todos" :checkChange="checkChange" :deleteItemById="deleteItemById"/>
    <TaskFooter v-if="this.todos.length" :todos="todos" :checkAll="checkAll" :clearTask='clearTask'/>
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
     todos: [
       {id: '001', title: '抽烟', done: false},
       {id: '002', title: '喝酒', done: true},
       {id: '003', title: '烫头', done: false}
     ]
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
  }
}
</script>

<style>

</style>
