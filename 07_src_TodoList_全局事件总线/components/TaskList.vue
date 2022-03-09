<template>
  <div>
    <ul>
      <TaskItem
        v-for="todoObj in todos"
        :key="todoObj.id"
        :todo="todoObj"
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
  props: ["todos"],
};
</script>
