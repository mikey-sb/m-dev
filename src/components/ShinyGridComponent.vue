<template>
    <div class="grid-container">
        <div id="cards">
            <div class="card">
                <div class="card-border"></div>
                <div class="card-content">

                </div>
                <div class="card-text">
                    <p>#</p>
                </div>
               
                <a href="/#/tile" class="link"></a>
            </div>
            <div class="card">
                <div class="card-border"></div>
                <div class="card-content"></div>
                <div class="card-text">
                    <p>~</p>
                </div>
               
                <a href="/#/tile" class="link"></a>
            </div>
            <div class="card">
                <div class="card-border"></div>
                <div class="card-content"></div>
                <div class="card-text">
                    <p>#</p>
                </div>
               
                <a href="/#/tile" class="link"></a>
            </div>
            <div class="card">
                <div class="card-border"></div>
                <div class="card-content"></div>
                <div class="card-text">
                    <p>~</p>
                </div>
               
                <a href="/#/tile" class="link"></a>
            </div>
            <div class="card">
                <div class="card-border"></div>
                <div class="card-content"></div>
                <div class="card-text">
                    <p>#</p>
                </div>
               
                <a href="/#/tile" class="link"></a>
            </div>
            <div class="card">
                <div class="card-border"></div>
                <div class="card-content"></div>
                <div class="card-text">
                    <p>~</p>
                </div>
               
                <a href="/#/tile" class="link"></a>
            </div>
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
    export default class ShinyGridComponent extends Vue {
        msg!: string;

        mounted(){

            
            const handleOnMouseMove = (e: Event)  => {
                const target = e.target as HTMLElement;
                const me = e as MouseEvent;


                const rect = target.getBoundingClientRect(),
                    x = me.clientX - rect.left,
                    y = me.clientY - rect.top;

                target.style.setProperty("--mouse-x", `${x}px`);
                target.style.setProperty("--mouse-y", `${y}px`);

                console.log(x, y)
            }

            for(const card of document.querySelectorAll(".card")){
                card.addEventListener("mousemove", (e) => {
                    handleOnMouseMove(e)
                }); 
            }

            var cards = document.getElementById("cards");
            if(cards){
                cards.addEventListener("mousemove", (e) => {
                    for(const card of document.querySelectorAll(".card")){
                        const carde = card as HTMLElement;
                        const me = e as MouseEvent;
                        
                        const rect = card.getBoundingClientRect(),
                            x = me.clientX - rect.left,
                            y = me.clientY - rect.top;

                        carde.style.setProperty("--mouse-x", `${x}px`);
                        carde.style.setProperty("--mouse-y", `${y}px`);
                    }
                })
            }

        }
        
    }
</script>

<style lang="scss">

:root{
    --bg-color: rgb(20,20,20);
    --card-color: rgb(23, 23, 23);
}

p{
    font-family: Arial, Helvetica, sans-serif;
    color: rgb(235,235,235,0.4);
    transition: color 0.3s ease-in-out;
}

.grid-container{
    width: 100vw;
    height: 100vh;
    background-color: var(--bg-color);
    display: flex;
    align-items:center;
    justify-content: center;
    margin: 0px;
    overflow: hidden;
    padding: 0px;
}

#cards{
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    max-width: 916px;
    width: calc(100% - 20px);
    
}

#cards:hover > .card > .card-border {
    opacity: 1;
}

.card {
    background-color: rgba(255, 255, 255, 0.1);
    height: 260px;
    width: 300px;
    border-radius: 10px;
    position: relative
}

.card:hover::before {
    opacity: 1;
}

.card::before,
.card > .card-border {
    background: radial-gradient(
        800px circle at var(--mouse-x) var(--mouse-y), 
        rgba(255, 255, 255, 0.06), 
        transparent 40%
    );
    position: absolute;
    content: "";
    border-radius: inherit;
    left: 0px;
    top: 0px;
    height: 100%;
    width: 100%;
    z-index: 2;
    opacity: 0;
    transition: opacity 500ms;
}

.card::before{
    background: radial-gradient(
        800px circle at var(--mouse-x) var(--mouse-y), 
        rgba(255, 255, 255, 0.06), 
        transparent 40%
    );
    z-index: 3;
}

.card > .card-border {
    background: radial-gradient(
        400px circle at var(--mouse-x) var(--mouse-y), 
        rgba(255, 255, 255, 0.3), 
        transparent 40%
    );
    z-index: 1;
}

.card > .card-content {
    background-color: var(--card-color);
    border-radius: 10px;
    z-index: 2;
    position: absolute;
    inset: 1px;
}

.card > a {
    width: 100%;
    height: 100%;
    z-index: 5;
    position: relative;
    display: flex;
}

.card-text{
    position: absolute;
    height: 100%;
    width: 100%;
    z-index: 2;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    background-color: transparent;
    
}

.card:hover p {
    color: rgb(235,235,235,0.9);
}

</style>
  