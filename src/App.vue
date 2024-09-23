<!-- COMPOSITION API -->
<script setup>
import { ref } from 'vue';


const name = ref('John Doe');
const status = ref('active');
const tasks = ref(['Task one', 'Task two', 'Task three']);

const toggleStatus = () => {
  if (status.value === 'active') {
    status.value = 'pending';
  } else if (status.value === 'pending') {
    status.value = 'inactive';
  } else {
    status.value = 'active';
  }
}

</script>

<template>
  <h1>Hello, my name is {{ name }}</h1>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is unactive</p>
  <h3>Task list:</h3>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul>
  <!-- <button v-on:click="toggleStatus()">Change status</button> -->
  <button @click="toggleStatus()">Change status</button>

</template>

<style scoped></style>
