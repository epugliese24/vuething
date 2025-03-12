<script setup>
// import { emits } from 'vue'
import axios from 'axios'
import TaskObj from '@/obj/TaskObj.js'
const emit = defineEmits(['deleteTask'])
const props = defineProps({
    name: {
        type: TaskObj,
        required: true,
    },
});
function deleteMe() {
    if (confirm("delete " + props.name.name)) {
        emit('deleteTask')
    }
}

</script>
<template>

    <button @click="deleteMe()">x</button> <span :class="{complete: name.isComplete}"@click="name.isComplete=!name.isComplete">{{ name.name }}</span>

</template>
<style scoped>
.complete{
    text-decoration: line-through;
    color:green;
}

</style>
