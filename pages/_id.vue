<template>
  <main class="re">
    <img :src="recipe.image" alt="food" />
    <h1>{{ recipe.title }}</h1>
    <p v-html="recipe.summary"></p>
    <h3>Steps</h3>
    <ul
      class="steps"
      v-for="stepbystep in steps"
      :key="stepbystep + Math.random()"
    >
      <li>{{ stepbystep.step }}</li>
    </ul>
  </main>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      recipe: {},
      steps: {},
    };
  },
  methods: {
    async fetchData() {
      let res = await axios.get(
        `https://api.spoonacular.com/recipes/${this.$route.params.id}/information?includeNutrition=false
&apiKey=${process.env.API_KEY}`
      );
      this.recipe = res.data;
      this.steps = res.data.analyzedInstructions[0].steps;
      console.log(typeof this.recipe.analyzedInstructions[0].steps);
    },
  },
  mounted() {
    this.fetchData();
  },
};
</script>

<style>
.re {
  width: 800px;
  margin: 0 auto;
  padding: 50px 0;
}

.re img {
  height: 400px;
  width: 100%;
  object-fit: cover;
}

.re h1,
h3,
p,
li {
  margin-top: 15px;
}
</style>
