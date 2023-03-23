<template>
  <div class="home">
    <!-- <GridRevealComponent msg="." /> -->
    <ShinyGridComponent msg="~" />

  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import LargeHeroComponent from "@/components/LargeHeroComponent.vue"; // @ is an alias to /src
import ShinyGridComponent from "@/components/ShinyGridComponent.vue"; // @ is an alias to /src
import GridRevealComponent from "@/components/GridRevealComponent.vue"; // @ is an alias to /src
import LargeHeroLogoComponent from "@/components/LargeHeroLogoComponent.vue"; // @ is an alias to /src
import ShortHeroComponent from "@/components/ShortHeroComponent.vue"; // @ is an alias to /src

@Options({
  components: {
    LargeHeroComponent,
    ShinyGridComponent,
    GridRevealComponent,
    LargeHeroLogoComponent,
    ShortHeroComponent,
  },
})
export default class HomeView extends Vue {}
</script>
