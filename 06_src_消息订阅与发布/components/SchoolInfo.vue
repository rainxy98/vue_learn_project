<template>
  <div class="school">
    <h2>学校名称: {{name}}</h2>
    <h2>学校地址: {{address}}</h2>
  </div>
</template>

<script>
import pubsub from 'pubsub-js';
export default {
  name: "SchoolInfo",
  data() {
    return {
      name: '清华',
      address: '北京'
    }
  },
  methods: {
    getName(msgName, data) {
      console.log('我是学校组件，收到了: ', msgName, data);
    }
  },
  mounted() {
    this.pubId = pubsub.subscribe('studentName', this.getName);
  },
  beforeDestroy() {
    pubsub.unsubscribe(this.pubId);
  }
}
</script>

<style scoped>
  .school {
    background-color: bisque;
  }
</style>
