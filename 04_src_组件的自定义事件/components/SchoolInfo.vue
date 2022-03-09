<template>
  <div class="school">
    <h2>学校名称: {{name}}</h2>
    <h2>学校地址: {{address}}</h2>
    <button @click="getName">点击获取学校名称</button>
  </div>
</template>

<script>
export default {
  name: "SchoolInfo",
  data() {
    return {
      name: '清华',
      address: '北京'
    }
  },
  props: ['getSchoolName'],
  methods: {
    getName() {
      this.getSchoolName(this.name);
    }
  }
}
</script>

<style scoped>
  .school {
    background-color: bisque;
  }
</style>
