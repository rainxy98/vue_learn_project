<template>
  <div class="student">
    <h2>学生姓名: {{ name }}</h2>
    <h2>学生年龄: {{ age }}</h2>
    <button @click="sendStudentName">点击发送学生姓名</button>
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
    sendStudentName() {
      this.$bus.$emit('studentName', this.name);
    },
    getName(name) {
      console.log('我是学生组件，我收到了：', name);
    }
  },
  mounted() {
    this.$bus.$on('schoolName', this.getName);
  },
  beforeDestroy() {
    this.$bus.$off('schoolName');
  }
};
</script>

<style scoped>
  .student {
    background-color:burlywood;
  }
</style>
