<template>
  <div>
    <ul>
      <TaskItem
        v-for="todoObj in todos"
        :key="todoObj.id"
        :todo="todoObj"
        :checkChange="checkChange"
        :deleteItemById='deleteItemById'
      />
    </ul>
  </div>
</template>

<script>
import TaskItem from "./TaskItem.vue";
export default {
  name: "TaskList",
  components: {
    TaskItem,
  },
  props: ["todos", "checkChange", "deleteItemById"],
};
</script>
