<template>
  <div>
    <form>
      <div class="form-group">
        <label for="name">Name:</label>
        <input class="form-control" type="text" v-model="name" placeholder="Type your name" />
        <br />

        <label for="email">E-Mail:</label>
        <input class="form-control" type="email" v-model="email" placeholder="Type your e-mail" />
        <br />

        <label for="date">Date of birth:</label>
        <input class="form-control" type="date" v-model="date" placeholder="Enter your birth date" />
      </div>

      <h5>Services</h5>
      <div class="form-check">
        <input
          class="form-check-input"
          id="1"
          name="services"
          type="checkbox"
          value="Processing - 1 micro - $ 1,00 per hour"
          v-model="services"
          @click="check($event)"
        />
        <label for="service1">Processing - 1 micro - $ 1,00 per hour</label>
        <br />

        <input
          class="form-check-input"
          id="2"
          name="services"
          type="checkbox"
          value="Processing - 1 medium - $ 2,00 per hour"
          v-model="services"
          @click="check($event)"
        />
        <label for="service2">Processing - 1 medium - $ 2,00 per hour</label>
        <br />

        <input
          class="form-check-input"
          id="3"
          name="services"
          type="checkbox"
          value="Processing - 1 large - $ 10,00 per hour"
          v-model="services"
          @click="check($event)"
        />
        <label for="service3">Processing - 1 large - $ 10,00 per hour</label>
        <br />

        <input
          class="form-check-input"
          id="4"
          name="services"
          type="checkbox"
          value="Storage - 10 GB HD - $ 0,5 per hour"
          v-model="services"
          @click="check($event)"
        />
        <label for="service4">Storage - 10 GB HD - $ 0,5 per hour</label>
        <br />

        <input
          class="form-check-input"
          id="5"
          name="services"
          type="checkbox"
          value="Storage - 1 TB HD - $ 1,00 per hour"
          v-model="services"
          @click="check($event)"
        />
        <label for="service5">Storage - 1 TB HD - $ 1,00 per hour</label>
        <br />

        <input
          class="form-check-input"
          id="6"
          name="services"
          type="checkbox"
          value="Storage - 100 GB SSD - $ 5,00 per hour"
          v-model="services"
          @click="check($event)"
        />
        <label for="service6">Storage - 100 GB SSD - $ 5,00 per hour</label>
      </div>

      <div>
        <button class="btn btn-primary btn-block" type="button" @click="clear()">CLEAR</button>
        <button
          class="btn btn-primary btn-block"
          type="button"
          @click="add(), persist()"
          v-on:click="count++"
        >ADD</button>
        <br />
      </div>
      <h5>
        <span class="badge badge-pill badge-primary">Cadastros realizados: {{ count }}</span>
      </h5>
    </form>
  </div>
</template>

<script>
export default {
  name: "inputTodo",
  props: {},

  data: function () {
    return {
      name: "",
      email: "",
      date: "",
      services: [],
      soma: 0,
      total: 0,
      count: 0,
    };
  },
  methods: {
    add: function () {
      var date = this.date;
      var dateInput = new Date(date);
      var dateAtual = new Date();
      var day = dateAtual.getDate() - dateInput.getDate();
      var month = dateAtual.getMonth() - dateInput.getMonth();
      var year = dateAtual.getFullYear() - dateInput.getFullYear();

      if (year >= 18) {
        let inputs = {};
        inputs.name = this.name;
        inputs.email = this.email;
        inputs.date = this.date;
        inputs.services = this.services;
        inputs.total = this.soma;

        this.tasks.push(inputs);

        this.total++;
      } else {
        window.alert("Cadastro realizado apenas com idade mínima de 18 anos!");
      }
    },
    check: function (serv) {
      if (serv.target.checked) {
        if (serv.target.id == 1) {
          this.soma += 1;
        }
        if (serv.target.id == 2) {
          this.soma += 2;
        }
        if (serv.target.id == 3) {
          this.soma += 10;
        }
        if (serv.target.id == 4) {
          this.soma += 0.5;
        }
        if (serv.target.id == 5) {
          this.soma += 1;
        }
        if (serv.target.id == 6) {
          this.soma += 5;
        }
      }
    },
    clear: function (serv) {
      this.name = "";
      this.email = "";
      this.date = "";
      this.services = [];
    },
    persist() {
      localStorage.Name = this.name;
      localStorage.Email = this.email;
      localStorage.Date_of_birth = this.date;
      localStorage.Services = this.services;
      localStorage.Quantidade_Cadastros = this.count;
    },
  },
  mounted() {
    if (localStorage.name) {
      this.name = localStorage.name;
    }
    if (localStorage.email) {
      this.email = localStorage.email;
    }
    if (localStorage.date) {
      this.date = localStorage.date;
    }
    if (localStorage.getItem("services")) {
      try {
        this.services = JSON.parse(localStorage.getItem("services"));
      } catch (serv) {}
    }
    if (localStorage.count) {
      this.count = localStorage.count;
    }
  }
};
</script>

<style>
</style>