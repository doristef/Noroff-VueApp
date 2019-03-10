<template>
    <div>
        <input class="input input-text" type="text" v-model="search" placeholder="Search by ingredient" />
        <button class="input input-search" type="button" @click="getRecipe()">Search for more!</button>
        <button class="input input-search" type="button" @click="getRecipe(true)">Reset!</button>
    </div>
</template>

<script>
export default {
  data() {
    return {
      search: ''
    }
  }
}
</script>