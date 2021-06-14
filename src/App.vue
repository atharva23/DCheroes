<template>
  <div class="container">
    <div class="row align-items-center">
      <h1>Dc heroes {{ herocount }}</h1>
      <h2>{{ fname }}{{ lname }}</h2>
      <p>{{ randc }}</p>
    </div>
    <ul>
      <li
        class="row justify-content-center"
        v-for="(hero, index) in dcheroes"
        :key="hero.name"
      >
        <div class="col-4">
          <p>{{ hero.name }}</p>
        </div>
        <div class="col-4">
          <button class="btn btn-primary" v-on:click="remove(index)">X</button>
        </div>
      </li>
    </ul>
    <div class="row">
      <div class="col-md-6 offset-md-3">
        <form @submit.prevent="addhero">
          <div class="input-group mb-3">
            <button
              class="btn btn-outline-secondary"
              type="submit"
              id="button-addon1"
            >
              Add hero
            </button>
            <input
              v-model="newhero"
              type="text"
              class="form-control"
              placeholder=""
              aria-label="Example text with button addon"
              aria-describedby="button-addon1"
            />
          </div>

          <!-- <button @click="newhero='wonder woman'">Add helero</button> -->
        </form>
      </div>
    </div>

    <small>total heroes in list {{ herocount }}</small>
  </div>
</template>

<script>
// import { push } from 'core-js/fn/array';
//import HelloWorldVue from "./components/HelloWorld.vue";
export default {
  name: "App",

  methods: {
    addhero() {
      if (this.newhero !== "") {
        this.dcheroes.unshift({ name: this.newhero });
        this.newhero = "";
      }
    },
    remove(index) {
      this.dcheroes = this.dcheroes.filter((hero, i) => i !== index);
    },
  },
  data() {
    return {
      fname: "ath",
      lname: "arva",
      isdisabled: false,
      newhero: "aquaman",
      dcheroes: [{ name: "batman" }, { name: "superman" }, { name: "flash" }],
    };
  },
  computed: {
    herocount() {
      return this.dcheroes.length;
    },
    randc() {
      return this.dcheroes.length + Math.random();
    },
    fullname: {
      get() {
        return "${this.fname}${this.lname}";
      },
    },
  },
  components: {},
};
</script>

<style>
</style>

