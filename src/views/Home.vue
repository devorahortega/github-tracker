<template>
  <div class="home">
    <h1>THIS IS THE GITHUB TRACKER</h1>
    <div v-for="repo in repos" v-bind:key="repo.id">
      <p>{{ repo.name }}</p>
      <p></p>
      <p></p>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";
import Vue2Filters from "vue2-filters";

export default {
  mixins: [Vue2Filters.mixin],
  name: "Home",
  data: function () {
    return {
      repos: [],
    };
  },
  methods: {
    repoIndex: function () {
      axios.get("https://github.com/repos/vuejs/vue").then((response) => {
        this.repos.push(response.data);
      });
      axios.get("https://github.com/repos/angular/angular.js").then((response) => {
        this.repos.push(response.data);
      });
      axios.get("https://github.com/repos/emberjs/ember.js").then((response) => {
        this.repos.push(response.data);
      });
      axios.get("https://github.com/repos/sveltejs/svelte").then((response) => {
        this.repos.push(response.data);
      });
      axios.get("https://github.com/repos/facebook/react").then((response) => {
        this.repos.push(response.data);
      });
    },
  },
};
</script>
