<template>
  <div class="todo-header">
    <input type="text" placeholder="请输入要添加的任务，按回车确认" v-model="title" @keyup.enter="add">
  </div>
</template>

<script>
import { nanoid } from 'nanoid';
export default {
  name: "TaskHeader",
  data() {
    return {
      title: ''
    }
  },
  methods: {
    add() {
      if (!this.title.trim()) {
        this.title = '';
        return alert('输入不能为空');
      }
      this.addTask({id: nanoid(), title: this.title, done: false});
      this.title = '';
      
    }
  },
  props: ['addTask']
}
</script>

<style scoped>
  .todo-header {
    background-color: skyblue;
  }
  .todo-header input {
    width: 200px;
  }
</style>
