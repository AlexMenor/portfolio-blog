<template>
  <div class="grid">
    <div class="proyect" v-for="proyect in $frontmatter.proyects">
      <img :src="proyect.image" :alt="proyect.name" />
      <p>{{ proyect.description }}</p>
    </div>
  </div>
</template>

<style scoped>
.grid {
  min-width: 100%;
  display: grid;
  grid-template-columns: repeat(auto-fill, 20em);
  grid-gap: 5em;
  justify-content: center;
  align-items: center;
}
.proyect img {
  max-width: 60%;
}
.proyect {
  border: solid #ccc 1px;
  padding: 2em;
  border-radius: 2em;
}
</style>
