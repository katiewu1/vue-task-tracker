<template>
  <!-- v-bind:key="task.id" -->
  <div :key="task.id" v-for="task in tasks">
    <!-- emit one step up to the App.vue (where we have access to the data) -->
    <Task
      @toggle-reminder="$emit('toggle-reminder', task.id)"
      @delete-task="$emit('delete-task', task.id)"
      :task="task"
    />
  </div>
</template>

<script>
import Task from "./Task";

export default {
  name: "Tasks",
  props: {
    tasks: Array,
  },
  components: {
    Task,
  },
  emits: ["delete-task", "toggle-reminder"],
};
</script>
