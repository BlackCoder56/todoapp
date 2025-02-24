<script setup>
    import { ref } from 'vue';

    const tasks = ref([]);
    
    const newTask = ref('');

    const addTask = () => {
          if(newTask.value.trim() !== '')
          {
              tasks.value.push(
                {name:newTask.value, status:'Pending'}
              );
              newTask.value = '';
          }
    };

    const deleteTask = (index) => {
          tasks.value.splice(index, 1);
    };

    const toggleStatus = (index) => {
         if(tasks.value[index].status === 'Pending'){
          tasks.value[index].status = 'Incomplete';
         }
         else if(tasks.value[index].status === 'Incomplete'){
          tasks.value[index].status = 'Complete';
         }
         else{
            tasks.value[index].status = 'Pending';
         }
    };  
</script>
<template>
    <h1>TODO Application</h1>

    <form @submit.prevent="addTask">
        <input type="text" name="newTask" placeholder="Enter new Task" v-model="newTask" />
        <button type="submit">Submit</button>
    </form>
    <br>
    <table v-if="tasks.length !== 0" border="1">
      <tr>
        <th>Task name</th>
        <th>Status</th>
        <th>Actions</th>
      </tr>
      <tr v-for="(task, index) in tasks" :key="task">
        <td>{{ task.name }}</td>
        <td>{{ task.status }}</td>
        <tr>
          <td>
          <button id="cs" @click="toggleStatus(index)">C:S</button>
        </td>
        <td>
          <button id="del" @click="deleteTask(index)">Delete</button>
        </td>
        </tr>        
      </tr>      
    </table>
    <span v-else>No Tasks for you Today!</span>
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
    /* font-size: 20px; */
    color:cadetblue;
  }

  table{
    border-collapse: collapse;
  }

  #del{
    margin: 2px;
    color: #fff;
    background-color: red;
  }

  #cs{
    color: #fff;
    background-color: blue;
  }

</style>