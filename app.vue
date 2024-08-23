<script setup>
const taskList = ref([{id: 1, title: "task 1", description: "description 1"}, {id: 2, title: "task 2", description: "description 2"}]);
</script>

<template>
  <div>
    <Task v-for="task in taskList" :key="task.id" :title="task.title" :description="task.description" />
  </div>
</template>