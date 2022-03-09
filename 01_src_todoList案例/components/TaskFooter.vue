<template>
  <div>
    <input type="checkbox" v-model='isAll'> 
    已完成{{doneTotal}}/全部{{todos.length}}
    <button @click="clearDoneTask">清除已完成任务</button>
  </div>
</template>

<script>
export default {
  name: "TaskFooter",
  props: ['todos', 'checkAll', 'clearTask'],
  computed: {
    doneTotal() {
      return this.todos.reduce((pre, cur) => pre + (cur.done ? 1 : 0), 0);
    },
    isAll: {
      get() {
        return this.todos.length == this.doneTotal && this.todos.length > 0;
      },
      set(value) {
        this.checkAll(value);
      }
    }
  },
  methods: {
    clearDoneTask() {
      this.clearTask();
    }
  }
}
</script>
