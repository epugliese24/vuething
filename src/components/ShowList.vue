<script setup>
defineProps({
  msg: {
    type: String,
    required: true,
  },
});

function openList() {
  console.log()
}

</script>

<template>
  <div class="greetings">
    <button @click="openList()" class="green" v-text="msg"></button>
  </div>
</template>