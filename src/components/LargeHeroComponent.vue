<template>
  <div class="hero-l-main-container">
    <div class="hero-l-bg-image">
      <img
        alt="paint"
        src="../assets/naples.webp"
        class="hero-l-bg-image-image"
      />
    </div>
    <div class="center hero-l__text-container">
      <h1 class="welcome">{{ msg }}</h1>
    </div>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";

@Options({
  props: {
    msg: String,
  },
})
export default class LargeHeroComponent extends Vue {
  msg!: string;
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
html {
  height: -webkit-fill-available;
}

body {
  margin: 0px;
}
.hero-l-main-container {
  position: relative;
}

.hero-l-bg-image-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  // padding: 1vw;
}

.hero-l-bg-image {
  width: 100vw;
  height: 100vh;
  overflow: hidden;
}

.center {
  position: absolute;
  margin-left: auto;
  margin-right: auto;
  left: 0;
  right: 0;
  text-align: center;
  top: calc(50vh - 25px);
}

.hero-l__text-container {
  height: 50px;
}

.welcome {
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
