<script setup>
const props = defineProps({
    title: String,
    description: String
});
</script>

<template>
    <div>
        <h2>{{ title }}</h2>
        <p>{{ description }}</p>
    </div>
</template>