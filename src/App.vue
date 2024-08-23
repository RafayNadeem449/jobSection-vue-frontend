<script setup>
  import { ref, onMounted } from "vue";

  const name = "Rafay"
  const tasks = ref(["Task 1","Task2", "Task 3"])
  const status= "pending"
  let newTask = ref("");

 
  function addTask()
  {
    if(newTask.value.trim() !== '')
    {
      tasks.value?.push(newTask.value);
      newTask.value='';
    }
  }
 

  const deleteTask = (index) => {
    tasks.value.splice(index,1);
  };


  onMounted(async ()=>{

    try{
      const response = await fetch('https://jsonplaceholder.typicode.com/todos');

      const data = await response.json();
      tasks.value = data.map((task)=>task.title);
    }
    catch(error)
    {
      
    }
  })

</script>



<template>
  <h1>Vue Jobs with {{name}}</h1>
  <p v-if="status">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is inactive</p>

  <form @submit.prevent="addTask">

    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask"/>
    <button type="submit">Submit</button>
  </form>


  <ul>
    <li v-for="(task,index) in tasks" :key="task">
      <span>{{ task }}</span>
      <button @click="deleteTask(index)">Delete</button>
      </li>
  </ul>

  <a v-bind:href="link"></a>
</template>

<style scoped>
</style>

