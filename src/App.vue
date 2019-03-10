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
.form {
    margin: 0 auto 50px auto;  
}
.input {
  margin: 10px;
  display: inline-block;
  border: 1px solid #333;
  border-radius: 10px;
  padding: 5px;
}

.input-text { width: 250px; height: 20px; }
.input-search { height: 30px; background: transparent;  }
.input-search:hover { background: #fd6a04; cursor: pointer; }

.recipe {
  display: inline-block;
  margin: 50px 15px;
  padding-bottom: 25px;
  width: 400px;
  border-bottom: 2px solid #333;
}

.recipe a, .recipe a:active, .recipe a:visited { color: #333;text-decoration: none; }
.recipe a:hover { color: #fd6a04; text-decoration: underline;}
.recipe img { max-width: 150px; width: 40%; max-height: 150px; height: 40%; border-radius: 15px; border: 1px solid #333;}

@media only screen and (max-width: 600px) {
  .recipe {
  margin: 35px 7px;
  padding-bottom: 20px;
  max-width: 400px;
  width: 85%;
}
}
</style>
