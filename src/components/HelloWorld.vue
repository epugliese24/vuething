<script setup>
defineProps({
  msg: {
    type: String,
    required: true,
  },
})
</script>

<template>
  <div>
    <h1 >{{ msg }}</h1>
    <h3>
      hjkdfhgjkdfhkjgfghfghhdfjkghkjfhdgfdchdghdfhfdhd
    </h3>
  </div>
</template>

<style scoped>
h1 {

  position: relative;

}



.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
