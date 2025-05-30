<template>
  <div class="container">
    <h2 class="text-center mt-5">TO-DO list</h2>
    <div class="d-flex">
      <input v-model="task" type="text" class="form-control rounded-0" placeholder="Введите текст">
      <button v-on:click="submitTask" class="btn btn-warning rounded-0">Отправить</button>
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
          <th>{{ task.name }}</th>
          <td>{{ task.status }}</td>
          <td>
            <div class="text-center">
              <span class="fa fa-pen"></span>
            </div>
          </td>
          <td>
            <div class="text-center">
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
    submitTask () {
      if(this.task.length === 0) return;

      this.tasks.push({
        name: this.task,
        status: 'Сделать'
      });
    }
  }
}
</script>

<style scoped>
</style>
