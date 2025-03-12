<script setup>
import axios from 'axios'
import { RouterLink, RouterView } from 'vue-router'
import TaskObj from '@/obj/TaskObj.js'
import Task from './components/Task.vue'
import { ref } from 'vue';
const listItems = ref([]);
const newMsg = ref("fdgd");
//adds list item
function addListItem() {
  if (newMsg.value != "") {
    let newTask = new TaskObj (newMsg.value);
    listItems.value.push(newTask);
    newMsg.value = ('')
  }
}
async function sendPost(objdata){
    axios.defaults.withCredentials = true;
    let params = new URLSearchParams();
    for (let key in objdata){
        params.append(key, objdata[key]);
    }

    const response = await axios.post("https://mclainonline.com/EdSuite/service.php", params);
    console.log(response);
    return response.data;
}

async function login(){

    const response = await sendPost({"rq": 10,
      "e": "epugliese27@riverdale.k12.or.us",
      "p": "test",
      "app": 3});
      if(response=="Success."){
        alert("logged in");
      }
      else{
        alert("fail")
      }
  
}
</script>

<template>
  <header>
<button @click="login()"></button>
    <div class="wrapper">
      <!-- adds list them -->
      <input type="text" placeholder="add new item" v-model="newMsg" />
      <button @click="addListItem()">+</button>
      <!-- shows list items -->
      <ul>
        <li v-for="listItem, index in listItems">
          <Task @deleteTask="listItems.splice(index, 1)" :name=listItem></Task>
        </li>
      </ul>

    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
