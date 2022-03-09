<template>
  <div class="student">
    <h2>学生姓名: {{ name }}</h2>
    <h2>学生年龄: {{ age }}</h2>
    <button @click="sendStudentName">点击发送学生姓名</button>
  </div>
</template>

<script>
import pubsub from 'pubsub-js'
export default {
  name: "StudentInfo",
  data() {
    return {
      name: '张三',
      age: 18
    }
  },
  methods: {
    sendStudentName() {
      pubsub.publish('studentName', this.name);
    }
  }
};
</script>

<style scoped>
  .student {
    background-color:burlywood;
  }
</style>
