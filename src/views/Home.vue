<template>
  <div class="home">
    <h1>THIS IS THE GITHUB TRACKER</h1>
    <div v-for="repo in orderBy(repos, 'forks_count', -1)" v-bind:key="repo.id">
      <p>{{ repo.name }}</p>
      <p>{{ repo.stargazers_count }}</p>
      <p>{{ repo.watchers_count }}</p>
      <p>{{ repo.forks_count }}</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Vue2Filters from "vue2-filters";

export default {
  mixins: [Vue2Filters.mixin],
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
