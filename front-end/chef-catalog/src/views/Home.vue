<template>
  <div class="home">
    <h1>This is the Home page</h1>
    <div class="all-chefs">
      <div class="you-info">
        <h2>Your recipes:</h2>
      </div>
      <div class="celeb-chef" v-for="chef in chefs" :key="chef._id">
        <h2>{{chef.name}}:</h2>
        <div class="recipe-list" v-for="recipe in getChefRecipes(chef)" :key="recipe._id">
          <h4>{{recipe.name}}</h4>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'Home',
  data() {
    return {
      chefs: [],
    }
  },
  created() {
    this.getChefs();
  },
  methods: {
    async getChefs(){
      try{
        let response = await axios.get("/api/chefs");
        this.chefs = response.data;
        console.log(this.chefs);
        return true;
      } catch (error) {
        console.log(error);
      }
    },
    async getChefRecipes(chef){
      try{
        let response = await axios.get("/api/chefs/"+chef._id+"/recipes");
        let recipes = response.data;
        console.log(recipes);
        this.recipes
        return recipes;
      } catch (error) {
        console.log(error);
      }
    }
  }
}
</script>

<style scoped>
.all-chefs{
  text-align: left;
}
.recipe-list{
  background-color: #00ff00;
}
</style>