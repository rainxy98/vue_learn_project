<template>
  <div id="app">
    <h1>{{msg}}</h1>
    <SchoolInfo :getSchoolName='getSchoolName'/>
    <StudentInfo ref="student"/>
  </div>
</template>

<script>
import SchoolInfo from './components/SchoolInfo.vue'
import StudentInfo from './components/StudentInfo.vue'

export default {
  name: 'App',
  data() {
    return {
      msg: '你好!!!'
    }
  },
  components: {
    SchoolInfo,
    StudentInfo
  },
  methods: {
    getSchoolName(name) {
      console.log('获取到学校名字: ', name);
    },
    getStudentName(name) {
      console.log('获取到了学生名字: ', name)
    }
  },
  mounted() {
    this.$refs.student.$on('getStudentName', this.getStudentName);
  }
}
</script>

<style scoped>
  #app {
    background-color: gray;
  }
</style>
