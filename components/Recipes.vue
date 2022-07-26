<template>
  <article>
    <div class="card" v-for="recipe in recipeArray" :key="recipe.id">
      <div class="card-img">
        <img :src="recipe.image" alt="title" />
        <div class="card-bottom">
          <h3>{{ recipe.title }}</h3>
          <p v-html="recipe.summary"></p>
          <button @click="loadRecipe">More info</button>
        </div>
      </div>
    </div>
  </article>
</template>

<script>
export default {
  methods: {
    loadRecipe() {
      console.log("first");
    },
  },
  props: ["recipeArray"],
};
</script>

<style>
.card {
  width: 250px;
  height: 450px;
  border: 1px solid rgba(0, 0, 0, 0.1);
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 4px 4px 25px rgba(0, 0, 0, 0.1);
  transition: 0.3s all ease;
  cursor: pointer;
}

.card:hover {
  transform: scale(1.025);
}

.card-img {
  height: 220px;
  width: 100%;
}
.card-img img {
  height: 100%;
  width: 100%;
  object-fit: cover;
  object-position: center;
}
.card-bottom {
  padding: 8px;
  position: relative;
  height: 230px;
}

.card-bottom button {
  cursor: pointer;
  margin: 0 auto;
  padding: 5px 10px;
  font-size: 20px;
  outline: none;
  border: none;
  background: lightslategrey;
  border-radius: 8px;
  color: white;
  position: absolute;
  bottom: 25px;
}
.card-bottom p {
  height: 80px;
  margin: 10px 0;
  overflow: hidden;
}

article {
  display: flex;
  padding: 20px 10px;
  gap: 20px;
  flex-wrap: wrap;
}
</style>
