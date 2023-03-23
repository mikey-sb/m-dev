<template>
  <div class="hero-s-main-container">
    <div class="">
      <h1 class="large-text">{{ bigText }}</h1>
    </div>
    <div class="">
      <h1 class="small-text">{{ smallText }}</h1>
    </div>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";

@Options({
  props: {
    bigText: String,
    smallText: String,
  },
})
export default class ShortHeroComponent extends Vue {}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.hero-s-main-container {
  position: relative;
}

.large-text {
  background-color: dodgerblue;
  height: 200px;
}

.small-text {
  background-color: hotpink;
  height: 100px;
}
</style>
