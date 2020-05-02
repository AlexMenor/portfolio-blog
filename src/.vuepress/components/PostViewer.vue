<template>
  <div>
    <div
      class="post-preview"
      v-for="post in pages"
      @click="$router.push(post.path)"
    >
      <h3>{{ post.title }}</h3>
      <p class="post-description">{{ post.frontmatter.description }}</p>
      <img class="post-image" :src="post.frontmatter.image" alt="Post image" />
    </div>
  </div>
</template>
<script>
export default {
  computed: {
    pages() {
      return this.$site.pages.filter((p) => p.frontmatter.type === "article");
    },
  },
};
</script>

<style scoped>
.post-preview {
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.post-preview:hover {
  cursor: pointer;
}
.post-description {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.post-image {
  object-fit: cover;
  max-height: 25em;
}
</style>
