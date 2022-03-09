<template>
  <div id="app">
    <h1>{{msg}}</h1>
    <SchoolInfo/>
    <StudentInfo/>
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
}
</script>

<style scoped>
  #app {
    background-color: gray;
  }
</style>
