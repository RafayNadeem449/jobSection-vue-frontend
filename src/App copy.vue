<script>
export default{
  data()
  {
    return{
      name:"Rafay",
      status:true,
      tasks:['Task One','Task 2', 'Task 3']
    }
  }
}

</script>


<template>
  <h1>Vue Jobs with {{name}}</h1>
  <p v-if="status">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is inactive</p>

  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul>

  <a v-bind:href="link"></a>
</template>

<style scoped>
</style>

