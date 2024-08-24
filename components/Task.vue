<script setup>
const props = defineProps({
    title: String,
    description: String,
    isComplete: Boolean
});
defineEmits(['deleteTask', 'taskStatus']);
</script>

<template>
    <div>
        <h2>{{ title }}</h2>
        <p>{{ description }}</p>
        <p>Status: </p>
        <button @click="$emit('taskStatus')">{{ isComplete ? 'Done' : 'Mark as Done' }}</button>
        <button @click="$emit('deleteTask')">Delete</button>
    </div>
</template>