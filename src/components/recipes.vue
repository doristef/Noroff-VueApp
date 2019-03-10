<template>
  <div class="container">
    <input class="input" type="text" v-model="search" placeholder="Search by ingredient" />

    <div class="recipe" v-for="recipe in getRecipe" :key="recipe.title">
      <a :href="recipe.href" :title="recipe.title"> 
        <img :src="recipe.thumbnail" /> 
        <h1>{{ recipe.title }}</h1>
      </a>
        <h4>Ingredients: </h4> <p> {{ recipe.ingredients }} </p>
    </div>
  
  </div>
</template>

<script>
import axios from 'axios';
const corsURL = "https://cors-anywhere.herokuapp.com/"; // Needed for Unblocking Cross-Origin request
const apiURL = "http://www.recipepuppy.com/api/"; // API to fetch from

export default {
  data() {
    return {
      recipes: [],
      errors: [],
      search: ''
    }
  },

  computed: {
    getRecipe() {
      return this.recipes.filter((recipe) => {
        return recipe.ingredients.toLowerCase()
        .indexOf(this.search.toLowerCase()) > -1;
      });
    }
  },

  created() {
    axios.get(corsURL + apiURL)
    .then(response => { this.recipes = response.data.results })
    .catch(e => {
      this.errors.push(e)
    })
  }


}
</script>