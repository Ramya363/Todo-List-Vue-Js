<template>
  <div class="container" style="max-width: 600px">
    
    <h2>My Vue Todo App</h2>

   <div>
      <input
        type="text"
        v-model="task"
        placeholder="Enter task"
        />
      <button class="btn" @click="submitTask">SUBMIT</button>
    </div>

    <!-- Task table -->
    <table class="table table-bordered mt-5">
      <thead>
        <tr>
          <th scope="col">Task</th>
          
          <th scope="col" class="text-center">Delete</th>
          <th scope="col" class="text-center">Edit</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" :key="index">
          <td>
            <span :class="{}">
              {{ task.name }}
            </span>
          </td>
         
          <td class="text-center">
            <div @click="deleteTask(index)">
             <button>Delete</button>
            </div>
          </td>
          <td class="text-center">
            <div @click="editTask(index)">
            <button>Edit</button> 
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  
  data() {
    return {
      task: "",
      editedTask: null,
      tasks: [],
    };
  },
  methods: {
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
    
    editTask(index) {
      this.task = this.tasks[index].name;
      this.editedTask = index;
    },
    
    submitTask() {
      if (this.task.length === 0) return;
      / We need to update the task /
      if (this.editedTask != null) {
        this.tasks[this.editedTask].name = this.task;
        this.editedTask = null;
      } else {
        / We need to add new task /
        this.tasks.push({
          name: this.task,
          });
      }
      this.task = "";
    },
  },
};
</script>

