<!-- COMPOSITION API -->
<script setup>
import { ref } from 'vue';


const name = ref('John Doe');
const status = ref('active');
const tasks = ref(['Task one', 'Task two', 'Task three']);
const newTask = ref('');

const toggleStatus = () => {
  if (status.value === 'active') {
    status.value = 'pending';
  } else if (status.value === 'pending') {
    status.value = 'inactive';
  } else {
    status.value = 'active';
  }
}

const addTask = () => {
  if(newTask.value.trim() !== ''){
    tasks.value.push(newTask.value);
    newTask.value = '';
  }
}

const deleteTask = (index) => {
  tasks.value.splice(index, 1);
};

</script>

<template>
  <h1>Hello, my name is {{ name }}</h1>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is unactive</p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask" />
    <button type="submit">Submit</button>
  </form>

  <h3>Task list:</h3>
  <ul>
    <li v-for="(task, index) in tasks" :key="task">
      <span>{{ task }}</span>
      <button @click="deleteTask(index)">X</button>
    </li>
  </ul>
  <!-- <button v-on:click="toggleStatus()">Change status</button> -->
  <button @click="toggleStatus()">Change status</button>

</template>

<style scoped></style>
