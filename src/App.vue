<template>
  <h1>Dc heroes {{ herocount }}</h1>
  <h2>{{ fname }}{{ lname }}</h2>
  <p>{{ randc }}</p>
  <ul>
    <li v-for="(hero, index) in dcheroes" :key="hero.name">
      <p>{{ hero.name }}<button v-on:click="remove(index)">X</button></p>
    </li>
  </ul>
  <form @submit.prevent="addhero">
    <input v-model="newhero" placeholder="type your hero" />
    <button type="submit">Add hero</button>
    <!-- <button @click="newhero='wonder woman'">Add helero</button> -->
  </form>
  <small>total heroes in list {{ herocount }}</small>
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

