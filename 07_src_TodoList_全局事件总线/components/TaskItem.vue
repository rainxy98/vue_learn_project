<template>
  <div>
    <li>
      <label>
        <input type="checkbox" :checked="todo.done" @change="handleChange(todo.id)">
        <span>{{todo.title}}</span>
      </label>
      <button @click="deleteItem(todo.id)">删除</button>
    </li>
  </div>
</template>

<script>
export default {
  name: "TaskItem",
  props: [
    'todo',
  ],
  methods: {
    handleChange(id) {
      this.$bus.$emit('checkChange', id);
    },
    deleteItem(id) {
      if (confirm('确定要删除吗？')) {
        this.$bus.$emit('deleteItemById', id);
      }
    }
  }
}
</script>

<style scoped>
  li label {
    float: left;
    cursor: pointer;
  }
  li label li input {
    vertical-align: middle;
    margin-right: 6px;
    position: relative;
    top: -1px
  }
  li button {
    float: right;
    margin-top: 3px;
    /* display: none; */
  }
  li :hover {
    background: gray;
  }
  li :hover button {
    display: block;
  }
</style>
