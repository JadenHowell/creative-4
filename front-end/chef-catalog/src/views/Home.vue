<template>
  <div class="home">
    <h1>This is the Home page</h1>
    <div class="all-chefs">
      <div class="you-info">
        <h2>Your recipes:</h2>
      </div>
      <div class="celeb-chef" v-for="chef in chefs" :key="chef._id">
        <h2>{{chef.name}}:</h2>
        <div class="recipe-list" v-for="recipe in recipes[chef.name]" :key="recipe._id">
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
      recipes: {},
    }
  },
  created() {
    this.loadAll();
  },
  methods: {
    async loadAll(){
      await this.loadChefs();
      for( let i = 0; i < this.chefs.length; i ++){
        this.loadRecipes(this.chefs[i]);
      }
    },
    async loadChefs(){
      try{
        let response = await axios.get("/api/chefs");
        this.chefs = response.data;
        console.log("in loadChefs, this,chefs: ", this.chefs);
        return true;
      } catch (error) {
        console.log(error);
      }
    },
    async loadRecipes(chef){
      try{
        let response = await axios.get("/api/chefs/"+chef._id+"/recipes");
        console.log(response.data);
        //this.$set triggers updates on the page whenever this deeper layer is created
        this.$set(this.recipes, chef.name, response.data);
        return true;
      } catch (error) {
        console.log(error);
      }
    },
  }
}
</script>

<style scoped>
.all-chefs{
  text-align: left;
}
</style>