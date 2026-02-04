<script setup>

import { onMounted, ref } from 'vue';

const name = ref("Natan Pereira");
const status = ref(true);
const tasks = ref(['Task One', 'Task Two', 'Task Three']);
const link = ref('https://google.com');
const newTask = ref('');

const changeStatus = () => {
  status.value = !status.value;
}

const addTask = () => {
  if(newTask.value.trim() !== ''){
    tasks.value.push(newTask.value);
    newTask.value = '';
  }
}

const deleteTask = (index) => {
  tasks.value.splice(index, 1);
}

onMounted(async () => {
  try{
    const response = await fetch('https://jsonplaceholder.typicode.com/todos');
    const data = await response.json();
    tasks.value = data.map((task) => task.title)
  } catch (error){
    console.log('Error')
  }
})

</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status">Status ok</p>
  <p v-else>Status no ok</p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label><br>
    <input type="text" id="newTask" name="newTask" v-model="newTask" />
    <button type="submit">Submit</button>
  </form>

  <h3>Tasks:</h3>
  <ul>
    <li v-for="(task, index) in tasks" :key="task" style="margin-top: 5px;">
      <span>
        {{ task }}
      </span>
      <button style="margin-left: 5px;" @click="deleteTask(index)">X</button>
    </li>
  </ul>
  <a v-bind:href="link">Click for google teste</a>

  <br>
  <button @click="changeStatus">Change</button>
</template>

