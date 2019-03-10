<template>
<div>
  <input type="text" />
  <button type="button"> Search </button>
  <article v-for="recipe in recipes" :key="recipe.title">
      <h1>{{ recipe.title }}</h1>
      <a :href="recipe.href" :title="recipe.title"> <img :src="recipe.thumbnail" /> </a>
      <p>{{ recipe.ingredients }}</p>
  </article>
</div>
</template>

<script>
import axios from 'axios';
const url = "https://cors-anywhere.herokuapp.com/"; // Needed for Unblocking Cross-Origin request
const apiUrl = "http://www.recipepuppy.com/api/";

export default {
  data() {
    return {
      recipes: [],
      errors: []
    }
  },

  created() {
    axios.get(url + apiUrl)
    .then(response => { this.recipes = response.data.results })
    .catch(e => {
      this.errors.push(e)
    })

  }
}
</script>