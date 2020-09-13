<template>
  <table class="table table-striped table-bordered table-condensed table-hover">
    <thead class="table-primary">
      <tr>
        <th scope="col">Name</th>
        <th scope="col">E-mail</th>
        <th scope="col">Date of birth</th>
        <th scope="col">Services</th>
        <th scope="col">Total</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(todo, index) in todos" v-bind:key="index">
        <td>
          <span>{{ todo.name }}</span>
        </td>
        <td>
          <span>{{ todo.email }}</span>
        </td>
        <td>
          <span>{{ todo.date }}</span>
        </td>
        <td>
          <span>{{ todo.services }}</span>
        </td>
        <td>
          <span>$ {{ todo.total }}</span>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: "tableTodo",
  props: ["todos"],
};
</script>

<style>
</style>