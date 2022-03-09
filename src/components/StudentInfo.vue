<template>
  <div class="student">
    <h2>学生姓名: {{ name }}</h2>
    <h2>学生年龄: {{ age }}</h2>
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
  }
};
</script>

<style scoped>
  .student {
    background-color:burlywood;
  }
</style>
