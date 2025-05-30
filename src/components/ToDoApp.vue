<template>
  <div class="container">
    <h2 class="text-center mt-5">TO-DO list</h2>
    <div class="d-flex">
      <input type="text" class="form-control rounded-0" placeholder="Введите текст">
      <button class="btn btn-warning rounded-0">Отправить</button>
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
        <tr>
          <th> Steal banans from the store</th>
          <td>Сделать</td>
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
  }
}
</script>

<style scoped>
</style>
