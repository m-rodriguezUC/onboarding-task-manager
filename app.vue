<script setup>
const taskList = ref([
  {id: 1, title: "task 1", description: "description 1", isComplete: false},
  {id: 2, title: "task 2", description: "description 2", isComplete: false}
]);
const titleText = ref("");
const descriptionText = ref("");
let nextId = taskList.value.length + 1;

const addNewTask = () => {
  console.log(taskList.value)
  taskList.value.push({id: nextId++, title: titleText.value, description: descriptionText.value, isComplete: false});
  titleText.value = "";
  descriptionText.value = "";
}

const deleteTask = (id) => {
  taskList.value = taskList.value.filter(task => task.id !== id);
}

const changeStatus = (id) => {
  taskList.value = taskList.value.map(task => {
    if(task.id === id) {
      task.isComplete = !task.isComplete;
    }
    return task;
  });
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
    <Task 
      v-for="task in taskList"
      :key="task.id"
      :title="task.title"
      :description="task.description"
      :isComplete="task.isComplete"
      @deleteTask="deleteTask(task.id)"
      @taskStatus="changeStatus(task.id)"
    />
  </div>
</template>