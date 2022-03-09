<template>
  <div class="school">
    <h2>学校名称: {{name}}</h2>
    <h2>学校地址: {{address}}</h2>
    <button @click="sendSchoolName">点击发送学校名称</button>
  </div>
</template>

<script>
import Vue from 'vue';
export default {
  name: "SchoolInfo",
  data() {
    return {
      name: '清华',
      address: '北京'
    }
  },
  methods: {
    sendSchoolName() {
      this.$bus.$emit('schoolName', this.name);
    },
    getName(name) {
      console.log('我是学校组件，收到了: ', name);
    }
  },
  mounted() {
    this.$bus.$on('studentName', this.getName);
  }
}
</script>

<style scoped>
  .school {
    background-color: bisque;
  }
</style>
