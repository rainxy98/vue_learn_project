<template>
  <div class="student">
    <h2>学生姓名: {{ name }}</h2>
    <h2>学生年龄: {{ age }}</h2>
    <button @click="getStudentName">点击获取学生姓名</button>
  </div>
</template>

<script>
export default {
  name: "StudentInfo",
  data() {
    return {
      name: '张三',
      age: 18
    }
  },
  methods: {
    getStudentName() {
      this.$emit('getStudentName', this.name);
    }
  }
};
</script>

<style scoped>
  .student {
    background-color:burlywood;
  }
</style>
