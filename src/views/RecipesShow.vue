<template>
  <div class="recipes-show">
    <h1>{{ recipe.title }}</h1>
    <h4>Chef: {{ recipe.chef }}</h4>
    <h4>Prep Time: {{ recipe.formatted.prep_time }}</h4>
    <h4>Ingredients: {{ recipe.ingredients }}</h4>
    <h4>Directions: {{ recipe.directions }}</h4>
  </div>
</template>

<style>
  
</style>

<script>
var axios = require('axios');

export default{
  data: function() {
    return {
      recipe: {
              id: "",
              title: "",
              chef:"Josh",
              ingredients: "",
              directions: "",
              prep_time:400,
              image_url: "",
              formatted:{
                ingredients: [],
                directions: [],
                prep_time: "",
                created_at: ""}
            }
    };
  },
  created: function() {
    axios.get("/api/recipes/" + this.$route.params.id)
      .then(response => {
        console.log(response.data);
        this.recipe = response.data;
      });
  },
  methods: {}
}
</script>