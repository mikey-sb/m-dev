<template>
  <div class="home">
    <ShinyGridComponent msg="~" />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import LargeHeroComponent from "@/components/LargeHeroComponent.vue"; // @ is an alias to /src
import ShinyGridComponent from "@/components/ShinyGridComponent.vue"; // @ is an alias to /src
import LargeHeroLogoComponent from "@/components/LargeHeroLogoComponent.vue"; // @ is an alias to /src
import ShortHeroComponent from "@/components/ShortHeroComponent.vue"; // @ is an alias to /src

@Options({
  components: {
    LargeHeroComponent,
    ShinyGridComponent,
    LargeHeroLogoComponent,
    ShortHeroComponent,
  },
})
export default class HomeView extends Vue {}
</script>
