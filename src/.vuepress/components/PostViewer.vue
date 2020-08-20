<template>
  <div class="post-viewer">
    <div class="post-preview" v-for="post in pages" @click="$router.push(post.path)">
      <h3>{{ post.title }}</h3>
      <p class="post-description">{{ post.frontmatter.description.substring(0,160) + '...' }}</p>
      <img class="post-image" :src="post.frontmatter.image" alt="Post image" />
      <div class="separator"></div>
    </div>
  </div>
</template>
<script>
export default {
  computed: {
    pages() {
      return this.$site.pages.filter(p => p.frontmatter.type === "article").reverse()
    }
  }
};
</script>

<style scoped>
.post-viewer {
  border-top: 1px solid grey;
}
.post-preview {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items:center;
}
.post-preview:hover {
  cursor: pointer;
}
.post-image {
  object-fit: cover;
  max-height: 25em;
}
.separator {
  margin-top:1em;
  border-bottom: 1px solid grey;
  width: 30%;
}
</style>
