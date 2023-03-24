<template>
    <div class="cursor"> 
    </div>
</template>
  
<script lang="ts">
    import { Options, Vue } from "vue-class-component";

    @Options({
        props: {
            color: String,
        },
    })
    export default class CursorComponent extends Vue {
        msg!: string;

        mounted(this :any){
            const cursor = document.querySelector('.cursor') as HTMLElement;
            cursor.style.backgroundColor = "" + this.color;
            // console.log(this.color)
            document.addEventListener('mousemove', (e) => {
                const em = e as MouseEvent;
                cursor?.setAttribute("style", "top: " + (em.pageY - 10) + "px; left: " + (em.pageX - 10) + "px; background-color: " + (this.color))
            });

            // cursor.addEventListener("click", (e) => {
            //     const em = e as MouseEvent;
            //     cursor.style.width = "60px";
            //     cursor.style.height = "60px";
            //     cursor.style.marginLeft = "-20px";
            //     cursor.style.marginTop = "-20px";
            //     setTimeout(() => { 
            //         cursor.style.width = "20px";
            //         cursor.style.height = "20px";
            //         cursor.style.marginLeft = "0px";
            //         cursor.style.marginTop = "0px"; 
            //     }, 500);
            // })



        }
    }
</script>

<style lang="scss">

:root{

}

.cursor{
    width: 20px;
    height: 20px;
    border: 1px solid white;
    border-radius: 50%;
    position: absolute;
    z-index: 4;
    // background-color: rgba(20,20,20, 0.8);
    transition: width, height, margin-left, margin-top 0.2s ease-in-out;

}


</style>
  