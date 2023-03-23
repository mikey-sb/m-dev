<template>
  <div class="hero-s-main-container">
    <div class="hero-s-bg-image">
      <img
        alt="paint"
        src="../assets/naples.webp"
        class="hero-s-bg-image-image"
      />
    </div>
    <div class="short-center hero-s-text-container">
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
export default class ShortHeroComponent extends Vue {
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

.hero-s-main-container {
  position: relative;
}

.hero-s-bg-image-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  // padding: 1vw;
}

.hero-s-bg-image {
  width: 100vw;
  height: 40vh;
  overflow: hidden;
}

.short-center {
  position: absolute;
  margin-left: auto;
  margin-right: auto;
  left: 0;
  right: 0;
  text-align: center;
  top: calc(20vh - 25px);
}

.hero-s-text-container {
  height: 50px;
}

.welcome {
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
