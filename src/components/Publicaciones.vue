<template>
<button v-on:click.prevent="mostrarpub">boton mostrar</button>
</template>

<script>
    export default{
       props:{
        listpubs: {
            type: Array
       },
        data(){
            return{
                titulo: this.titulo
            }
            
        },
        methods:{
            mostrarpub(){
                console.log(this.listpubs)
            }
            
        }
    }
}
</script>

<style>

</style>