<template>
  <!-- Ternary operator, if task.reminder is true ? add class 'reminder' : otherwise none. 
But every task will have the class 'task' -->
  <div
    @dblclick="$emit('toggle-reminder', task.id)"
    :class="[task.reminder ? 'reminder' : '', 'task']"
  >
    <h3>
      {{ task.text }}
      <!-- Can also use this with the method onDelete() -->
      <!-- <i @click="onDelete(task.id)" class="fas fa-times"></i> -->

      <!-- emit one step up to the Tasks.vue -->
      <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
    </h3>
    <p>{{ task.day }}</p>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
  //   methods: {
  //     onDelete(id) {
  //       //   console.log(id);
  //       // emit one step up to the Tasks.vue
  //       this.$emit("delete-task", id);
  //     },
  //   },
};
</script>

<style scoped>
/* font-awesome */
.fas {
  color: red;
}
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.task.reminder {
  border-left: 5px solid green;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
