<template>
  <div class="home-page-content">
    <div>
      <h1>
        {{currentConsoleText}}
        <span v-if="showUnderscore" id="console-underscore">&#95;</span>
      </h1>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showUnderscore: false,
      consoleText: "I like to do Backend Development",
      typePosition: 0,
      typeInterval: null
    };
  },
  mounted() {
    setInterval(this.switchUnderscoreState, 400);
    this.typeInterval = setInterval(this.stochasticTyping, 100);
  },
  methods: {
    switchUnderscoreState() {
      this.showUnderscore = !this.showUnderscore;
    },
    stochasticTyping() {
      if (Math.random() < 0.8) this.typePosition++;
      if (this.typePosition == this.consoleText.length)
        clearInterval(this.typeInterval);
    }
  },
  computed: {
    currentConsoleText() {
      return this.consoleText.slice(0, this.typePosition);
    }
  }
};
</script>

<style scoped>
.home-page-content {
  padding: 0.5rem 1rem;
}
</style>