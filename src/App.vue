<template>
  <div id="app">
    <recipes />
  </div>
</template>

<script>
import recipes from './components/recipes.vue'

export default {
  name: 'app',
  components: {
    recipes
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.container {
  max-width: 1000px;
  width: 100%;
  margin: 0 auto;
}

.input {
  display: block;
  margin: 50px auto;  
  width: 250px;
  height: 20px;
  border: 1px solid #333;
  border-radius: 10px;
  padding: 5px;
}

.recipe {
  display: inline-block;
  margin: 50px 25px;
  padding-bottom: 25px;
  width: 450px;
  border-bottom: 2px solid #333;
}

.recipe a, .recipe a:active, .recipe a:visited { color: #333;text-decoration: none; }
.recipe a:hover { color: #fd6a04; text-decoration: underline;}
.recipe img { max-width: 150px; width: 40%; max-height: 150px; height: 40%; border-radius: 15px; border: 1px solid #333;}
</style>
