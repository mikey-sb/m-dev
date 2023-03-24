<template>
  <div class="home">
    <!-- <GridRevealComponent msg="." /> -->
    <ShinyGridComponent msg="~" />
    <CursorComponent color="rgba(20,20,20, 0.8);"/>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import LargeHeroComponent from "@/components/LargeHeroComponent.vue"; // @ is an alias to /src
import ShinyGridComponent from "@/components/ShinyGridComponent.vue"; // @ is an alias to /src
import GridRevealComponent from "@/components/GridRevealComponent.vue"; // @ is an alias to /src
import LargeHeroLogoComponent from "@/components/LargeHeroLogoComponent.vue"; // @ is an alias to /src
import ShortHeroComponent from "@/components/ShortHeroComponent.vue"; // @ is an alias to /src
import CursorComponent from "@/components/CursorComponent.vue"; // @ is an alias to /src

@Options({
  components: {
    LargeHeroComponent,
    ShinyGridComponent,
    GridRevealComponent,
    LargeHeroLogoComponent,
    ShortHeroComponent,
    CursorComponent
  },
})
export default class HomeView extends Vue {}
</script>

<style lang="scss">
  body{
    background-color: rgb(20,20,20);
  }
  body, a{
    cursor: none;
  }
  .home{
    .cursor{
      opacity: 1;
    }
  }
</style>