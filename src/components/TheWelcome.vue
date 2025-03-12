<script setup>
import ShowList from './ShowList.vue'
import { ref } from 'vue';
const openReadmeInEditor = () => fetch('/__open-in-editor?file=README.md')
const lists = ref([]);
const newMsg = ref("fdgd");
// adds new list button and logs it
function newList() {
  console.log(newMsg.value)
  if (newMsg.value != "") {
    lists.value.push(newMsg.value);
    newMsg.value = ('')
  }
}

</script>

<template>
  <div>
    see all lists<br>
    <!-- new list input -->
    <input type="text" placeholder="add new list" v-model="newMsg" />
    <button @click="newList()">+</button>
    {{ newMsg }}
    <!-- list list -->
    <ShowList v-for="list in lists" :msg="list" />

  </div>
</template>
