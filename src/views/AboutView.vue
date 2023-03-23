<template>
  <div class="about">
    <ShortHeroComponent msg="-" />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import ShortHeroComponent from "@/components/ShortHeroComponent.vue"; // @ is an alias to /src

@Options({
  components: {
    ShortHeroComponent,
  },
})
export default class AboutView extends Vue {}
</script>
