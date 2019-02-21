<template>
  <div class="recipes-index">
    <h1>All Recipes</h1>
    
    <div class="row">
      <div class="col-md-4" v-for="recipe in recipes">
        <div class="card">
          <router-link v-bind:to="'/recipes/' + recipe.id">
            <img class="card-img-top" v-bind:src="recipe.image_url" v-bind:alt="recipe.title">
          </router-link>
          <div class="card-body">
            <h5 class="card-title">
              {{ recipe.title }}
            </h5>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<style>
</style>

<script>
var axios = require('axios');
export default {
  data: function() {
    return {
      recipes: [],
      currentRecipe: {}
    };
  },
  created: function() {
    axios.get("/api/recipes")
      .then(response => {
        this.recipes = response.data;
      });
  },
  methods: {}
};
</script>
