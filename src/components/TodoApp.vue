<template>
  <div class="container">
    <h2 class="text-center mt-5">Vue Todo App</h2>

    <!---------------------- Input ------------------->
    <div class="d-flex">
      <input v-model="task" type="text" placeholder="Enter task" class="form-control">
      <button @click="sumitTask" class="btn btn-warning rounded-0">SUBMIT</button>
    </div>
    <!---------------------- Task Table ------------------->
    <table class="table table-bordered mt-5">
      <thead>
        <tr>
          <th scope="col">Task</th>
          <th scope="col" class="text-center">Edit</th>
          <th scope="col" class="text-center">Delete</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in tasks" :key="index">
          <td>{{ item.name }}</td>
          <td>
            <div class="text-center pointer" @click="updateTask(index)">
              <span class="fa fa-pen"></span>
            </div>
          </td>
          <td>
            <div class="text-center pointer" @click="deleteTask(index)">
              <span class="fa fa-trash"></span>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'TodoApp',
  data() {
    return {
      task: '',
      updatedTask: null,
      tasks: [
        {
          name: 'Steal bananas from the store.',
        },
        {
          name: 'Eat 1kg chocolate in 1 hour.',
        },
        {
          name: 'Steal bananas from the store.',
        },
        {
          name: 'Eat 1kg chocolate in 1 hour.',
        },
        {
          name: 'Steal bananas from the store.',
        },
        {
          name: 'Eat 1kg chocolate in 1 hour.',
        },
        {
          name: 'Steal bananas from the store.',
        },
        {
          name: 'Eat 1kg chocolate in 1 hour.',
        }
      ]
    }
  },

  methods: {
    sumitTask() {
      if(this.task.length === 0) return;

      if(this.updatedTask === null){

        this.tasks.push({
          name: this.task,
          status: 'to-do'
        });
      }else{
        this.tasks[this.updatedTask].name = this.task;
        this.updatedTask = null;
      }
      this.task = '';
    },


    deleteTask(index) {
      this.tasks.splice(index, 1)
    },
    updateTask(index) {
      this.task = this.tasks[index].name;
      this.updatedTask = index;
    }
  }
}
</script>

<style scoped>
.pointer{
  cursor: pointer;
}
</style>