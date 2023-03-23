<template>
    <div id="tiles"></div>

<h1 id="title" class="centered">

</h1>

<i id="icon" class="fa-solid fa-chess centered"></i>
<div class="shiny-grid-cmp">
</div>
</template>
  
<script lang="ts">
    import ShinyGridComponent from "@/components/ShinyGridComponent.vue";
    import { Options, Vue } from "vue-class-component";
    import anime from 'animejs';

    @Options({
        components: {
            ShinyGridComponent
        },
        props: {
            msg: String,
        },
    })
    export default class GridRevealComponent extends Vue {
        msg!: string;

        mounted(){ 
            const wrapper = document.getElementById("tiles");

let columns = 0,
    rows = 0,
    toggled = false;

const toggle = () => {
  toggled = !toggled;
  
  document.body.classList.toggle("toggled");
}

const handleOnClick = (index: any) => {
  toggle();
  
  anime({
    targets: ".tile",
    opacity: toggled ? 0 : 1,
    delay: anime.stagger(50, {
      grid: [columns, rows],
      from: index
    })
  });
}

const createTile = (index: number) => {
  const tile = document.createElement("div");
  
  tile.classList.add("tile");
  
  tile.style.opacity = `${toggled ? 0 : 1}`;
  
  tile.onclick = e => handleOnClick(index);
  
  return tile;
}

const createTiles = (quantity: number) => {
  Array.from(Array(quantity)).map((tile, index) => {
    if(wrapper)
    wrapper.appendChild(createTile(index));
  });
}

const createGrid = () => {
    if(wrapper)
  wrapper.innerHTML = "";
  
  const size = document.body.clientWidth > 800 ? 100 : 50;
  
  columns = Math.floor(document.body.clientWidth / size);
  rows = Math.floor(document.body.clientHeight / size);
  if(wrapper)
  wrapper.style.setProperty("--columns", `${columns}`);
  if(wrapper)
  wrapper.style.setProperty("--rows", `${rows}`);
  
  createTiles(columns * rows);
}

createGrid();

window.onresize = () => createGrid();
        }
        
    }
</script>

<style lang="scss" scoped>

:root {
  --g1: rgb(98, 0, 234);
  --g2: rgb(236, 64, 122);
}

@keyframes background-pan {
  from {
    background-position: 0% center;
  }
  
  to {
    background-position: -200% center;
  }
}

body {
  animation: background-pan 10s linear infinite;
  background: linear-gradient(
    to right,
    var(--g1),
    var(--g2),
    var(--g1)
  );
  background-size: 200%;
  height: 100vh;
  overflow: hidden;
  margin: 0px;
}

body.toggled {
  animation: none;
}

body.toggled > #title {
  opacity: 0;
}

body.toggled > #icon {
  opacity: 1;
}

body.toggled > #tiles > .tile:hover {
  opacity: 0.1 !important;
}

.centered {
  left: 50%;
  position: absolute;
  top: 50%;
  transform: translate(-50%, -50%);
}

#tiles {
  height: calc(100vh - 1px);
  width: calc(100vw - 1px);
  position: relative;
  z-index: 1;
  
  display: grid;
  grid-template-columns: repeat(var(--columns), 1fr);
  grid-template-rows: repeat(var(--rows), 1fr);
}

.tile {
  cursor: pointer;
  position: relative;
}

.tile:hover:before {
  background-color: rgb(30, 30, 30);
}

.tile:before {
  background-color: rgb(15, 15, 15);
  content: "";
  inset: 0.5px;
  position: absolute;
}

#title {
  color: white;
  font-family: "Rubik", sans-serif;
  font-size: 6vw;
  margin: 0px;
  pointer-events: none;
  transition: opacity 1200ms ease;
  width: 50vw;
  z-index: 2;
}



.shiny-grid-cmp{
    position: absolute;
    top: 0;
    
}
</style>
  