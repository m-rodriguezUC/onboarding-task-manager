<script setup>
const taskList = ref([{id: 1, title: "task 1", description: "description 1"}, {id: 2, title: "task 2", description: "description 2"}]);
const titleText = ref("");
const descriptionText = ref("");

let addNewTask = () => {
  taskList.value.push({id: taskList.value.length + 1, title: titleText.value, description: descriptionText.value});
  titleText.value = "";
  descriptionText.value = "";
}
</script>

<template>
  <div>
    <form v-on:submit.prevent="addNewTask">
      <label>Title</label>
      <input v-model="titleText" placeholder="add title here" />
      <label>Description</label>
      <input v-model="descriptionText" placeholder="add description here" />
      <button>Add Task</button>
    </form>
    <Task v-for="task in taskList" :key="task.id" :title="task.title" :description="task.description" />
  </div>
</template>