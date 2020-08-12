<template>
  <div class="home-page-content">
    <div class="console-block">
      <h1>
        {{ currentConsoleText }}
        <span v-if="showUnderscore" id="console-underscore">&#95;</span>
      </h1>
    </div>
    <h2>About me</h2>
    <p>I'm a {{ age }} year old Computer Engineering student from Spain.</p>
    <p>
      After 2 years studying my degree, I found in Web and Mobile Development my
      passion. More specifically: Server Side Programming, Cloud Computing and
      API Design.
    </p>
    <p>
      I'm right now working at
      <a href="https://pantala.es">Pantala</a> while I finish my degree. I'm
      also the lead of
      <a href="https://developers.google.com/community/dsc">DSC</a> in Granada.
    </p>
    <h2>Some of the technologies I enjoy the most are</h2>
    <ul>
      <li>NodeJS with NestJS as a framework</li>
      <li>Spring Boot</li>
      <li>PostgreSQL and MongoDB</li>
      <li>GoLang</li>
      <li>Vue</li>
      <li>Flutter</li>
    </ul>
    <h2>Projects that I've been working on</h2>
    <ProjectViewer />
  </div>
</template>

<script>
export default {
  data() {
    return {
      showUnderscore: false,
      consoleText: "I like to do Backend Development.",
      typePosition: 0,
      typeInterval: null,
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
    },
  },
  computed: {
    currentConsoleText() {
      return this.consoleText.slice(0, this.typePosition);
    },
    age() {
      const birthday = new Date("02/10/1999");
      const diff = Date.now() - birthday;
      const ageDate = new Date(diff);
      return Math.abs(ageDate.getUTCFullYear() - 1970);
    },
  },
};
</script>

<style scoped>
.home-page-content {
  padding: 0.5rem 1rem;
}
.console-block {
  padding-top: 5em;
  padding-bottom: 5em;
}
</style>
