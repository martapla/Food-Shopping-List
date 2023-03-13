<script setup>

const props = defineProps({
    todo: {
        type: Object,
        required: true,
    },
});

</script>

<template>
    <li>
        <input type="checkbox" :checked="todo.isCompleted">
    </li>
</template>