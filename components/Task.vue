<script setup>
const props = defineProps({
    title: String,
    description: String
});
defineEmits(['deleteTask']);
</script>

<template>
    <div>
        <h2>{{ title }}</h2>
        <p>{{ description }}</p>
        <button @click="$emit('deleteTask')">Delete</button>
    </div>
</template>