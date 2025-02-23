<script setup>
    import { ref } from 'vue';

    const tasks = ref(['Orange', 'Mango', 'Apple']);

</script>
<template>
    <h1>TODO Application</h1>

    <form @submit.prevent="">
        <input type="text" name="newTask" placeholder="Enter new Task" />
        <button type="submit">Submit</button>
    </form>
    <br>
    <table border="1">
     <tr>
      <!-- <th>No.</th> -->
        <th>Task name</th>
        <th>Status</th>
        <th>Actions</th>
     </tr>
     <tr v-for="(task, index) in tasks">
        <!-- <td>{{ index }}</td> -->
        <td>{{ task }}</td>
     </tr>
    </table>
</template>

<style scoped>
  h1{
    text-decoration: underline;
  }
  input{
    font-size: 20px;
    margin-right: 10px;
  }

  button{
    font-size: 20px;
    color:cadetblue;
  }

  table{
    border-collapse: collapse;
  }

</style>