<template>
  <div>
    <header>
      <img alt="RecipeShare Logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
      <h1>Welcome to RecipeShare! 😋</h1>
    </header>
    <main>
      <div class="recipe-list">
        <div class="recipe-card" v-for="(recipe, index) in recipes" :key="index">
          <h2>{{ recipe.title }}</h2>
          <p>{{ recipe.description }}</p>
          <button @click="voteForRecipe(index)">Vote</button>
          <button @click="undoVote(index)" v-if="recipe.votes > 0">Undo Vote</button>
          <p>Votes: {{ recipe.votes }}</p>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      recipes: [
        { id: 1, title: 'Macarona Bechamel', description: 'Delicious unique pasta dish.', votes: 0 },
        { id: 2, title: 'Nutella Kunafa', description: 'Bussing chocolate dessert.', votes: 0 },
        { id: 3, title: 'Shish Barak ', description: 'Yummy Lebanese dish.', votes: 0 },
      ],
    };
  },
  methods: {
    voteForRecipe(index) {
      // Increase the vote count for the selected recipe
      this.recipes[index].votes++;
    },
    undoVote(index) {
      // Decrease the vote count for the selected recipe if votes are greater than 0
      if (this.recipes[index].votes > 0) {
        this.recipes[index].votes--;
      }
    },
  },
}
</script>

<style scoped>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
}

header {
  background-color: #007bff;
  color: white;
  padding: 20px;
  text-align: center;
}

.logo {
  display: block;
  margin: 0 auto;
}

h1 {
  font-size: 24px;
  margin-top: 10px;
}

/* Styles for recipe list */
.recipe-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

/* Styles for recipe card */
.recipe-card {
  background-color: #f4f4f4;
  padding: 10px;
  margin: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}

/* Styles for responsive design */
@media (max-width: 768px) {
  header {
    padding: 10px;
  }

  h1 {
    font-size: 20px;
  }

  .logo {
    width: 100px;
    height: 100px;
  }
}
</style>
