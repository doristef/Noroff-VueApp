<template>
  <div class="container">
    <div class="form">
      <h4> You can type in ingredients to find recipes in the list, or click the button to get more recipes with given ingredient</h4>
      <p><i>You can search for multiple ingredients, just remember to put a colon (,) between!</i></p>
      <input class="input input-text" type="text" v-model="search" placeholder="Search by ingredient" />
      <button class="input input-search" type="button" @click="getRecipe()">Search for more!</button>
      <button class="input input-search" type="button" @click="getRecipe(true)">Reset!</button>
    </div>
    <h2 v-if="loading">Loading....</h2>
    <div v-else class="recipe" v-for="(recipe, i) in getRecipeFiltered" :key="i">
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
      search: '',
      loading: true
    }
  },

  computed: {
    getRecipeFiltered() {
      return this.recipes.filter((recipe) => {
        return recipe.ingredients.toLowerCase()
        .indexOf(this.search.toLowerCase()) > -1;
      });
    }
  },

  methods: {
    getRecipe: function(fresh) {
      this.loading = true;
      if(fresh){ this.search = ''; }
      this.apiCall();
      },

    apiCall: function() {
      axios.get(corsURL + apiURL + '?i=' + this.search)
        .then(response => { this.recipes = response.data.results; this.loading = false; })
        .catch(e => { this.errors.push(e) })
    }
  },

  created() {
    this.apiCall();
  }
}
</script>