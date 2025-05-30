<template>
  <div class="container">
    <h2 class="text-center mt-5">TO-DO list</h2>
    <div class="d-flex">
      <input v-model="task" type="text" class="form-control rounded-0" placeholder="Введите текст">
      <button v-on:click="submitTask" class="btn btn-warning rounded-0 pointer">Отправить</button>
    </div>
    <table class="table table-bordered mt-5">
      <thead>
        <tr>
          <th scope="col">Задача</th>
          <th scope="col">Статус</th>
          <th scope="col" class="text-center">#</th>
          <th scope="col" class="text-center">#</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, id) in tasks" :key="id">
          <th>
            <span :class="{'finished' : task.status === 'Завершено'}">
              {{ task.name }}
            </span>
          </th>
          <td style="width: 200px;">
            <span v-on:click="changeStatus(id)" class="pointer" :class="{'text-red' : task.status === 'Сделать', 'text-yellow': task.status === 'В работе'}">
              {{ task.status }}
            </span>
          </td>
          <td>
            <div class="text-center" v-on:click="editTask(id)">
              <span class="fa fa-pen"></span>
            </div>
          </td>
          <td>
            <div class="text-center" v-on:click="deleteTask(id)">
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
  name: 'ToDoApp',
  props: {
    msg: String
  },
  data () {
    return {
      task: '',
      editedTask: null,
      availableStatuses: ['Сделать', 'В работе', 'Завершено'],
      tasks: [
      {
        name: 'Steal banans from the store',
        status: 'Сделать',
      },
      {
        name: 'Eat 1 kg chocolate in 1 hour',
        status: 'В работе',
      }
    ]
    }
  },
  methods: {
    submitTask() {
      if(this.task.length === 0) return;

      if(this.editedTask === null) {
        this.tasks.push({
          name: this.task,
          status: 'Сделать'
        });
      }else {
        this.tasks[this.editedTask].name = this.task;
        this.editedTask = null;
      }

      this.task = '';
    },
    deleteTask(id) {
      this.tasks.splice(id, 1);
    },
    editTask(id) {
      this.task = this.tasks[id].name;
      this.editedTask = id;
    },
    changeStatus(id) {
      let newId = this.availableStatuses.indexOf(this.tasks[id].status);

      if(++newId > 2) {
        newId = 0;
      }

      this.tasks[id].status = this.availableStatuses[newId];
    },
  }
}
</script>

<style scoped>
.pointer {
  cursor: pointer;
}
.finished {
  text-decoration: line-through;
}
.text-red {
  color: #fa2222;
}
.text-yellow {
  color: yellow;
}
</style>
