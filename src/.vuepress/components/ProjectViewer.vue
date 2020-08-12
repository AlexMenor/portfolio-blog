<template>
  <div class="grid">
    <div class="project" v-for="project in $frontmatter.projects">
      <img :src="project.image" :alt="project.name" />
      <p>{{ project.description }}</p>
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
.project img {
  max-width: 60%;
}
.project {
  border: solid #ccc 1px;
  padding: 2em;
  border-radius: 2em;
}
.project p {
  line-height: 2;
}
</style>
