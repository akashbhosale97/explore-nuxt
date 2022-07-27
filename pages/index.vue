<template>
  <main>
    <h1 class="main-title">Recipe Search</h1>
    <form @submit.prevent="fetchData">
      <input
        type="text"
        v-model="query"
        placeholder="Enter a recipe to search"
      />
      <button type="submit">Search</button>
    </form>
    <Recipes :recipeArray="recipes" />
  </main>
</template>

<script>
import axios from "axios";
import Recipes from "../components/Recipes";
export default {
  components: {
    Recipes,
  },
  data() {
    return {
      recipes: [],
      query: "",
    };
  },
  methods: {
    async fetchData() {
      let res = await axios.get(
        `https://api.spoonacular.com/recipes/complexSearch?query=${this.query}&addRecipeInformation=true&addRecipeNutrition=true&number=20&apiKey=${process.env.API_KEY}`
      );
      this.recipes = res.data.results;
    },
  },
  mounted() {
    this.fetchData();
  },
};
</script>

<style>
.main-title {
  text-align: center;
  margin: 20px 0;
}

form {
  display: flex;
  justify-content: center;
  flex-direction: column;
  width: 300px;
  margin: 0 auto;
}

form input {
  width: 100%;
  height: 40px;
  font-size: 24px;
  outline: none;
  border: 1px solid #ccc;
  border-radius: 8px;
  text-indent: 10px;
  margin-bottom: 15px;
}

form button {
  cursor: pointer;
  margin: 0 auto;
  width: 50%;
  height: 40px;
  font-size: 24px;
  outline: none;
  border: none;
  background: lightslategrey;
  border-radius: 8px;
  color: white;
  margin-bottom: 15px;
}
</style>
