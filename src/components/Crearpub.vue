<template>

    <div class="publicacion" v-if="visible=== false">
        <form action="" v-on:submit.prevent="enviar">
            <input required type="text" placeholder="Titulo de la Publicacion" v-model="titulo">
            <textarea required type="text" placeholder="Contenido de la Publicacion" v-model="cuerpo"></textarea>
            <button type="submit" >Crear Publicaciones</button>
            <button v-on:click.prevent="display">Cancelar</button>
        </form>
    </div>

    


</template>

<script>


export default{
    data(){
        return{
            titulo:'',
            cuerpo: '',
            posts: [],
            visible: false
        }
    },
    methods:{
        CrearPubli(){
            this.titulo= '',
            this.cuerpo=''
           this.visible=true
        },
        display(){
            if(!this.visible){
              this.visible = true;
            } else{
              this.visible = false;
            }
          },
        enviar(){
            
            this.$emit('send', this.titulo)
            this.$emit('send', this.cuerpo)

            this.cuerpo='';
            this.titulo= '';
        }

    }

    
}
</script>

<style>

.publicacion{
    width: 100vw;
    height: calc(100vh - 80px);
    margin-top: 80px;
}
.publicacion form{
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-content: center;
    position: absolute;
    width: 80%;
    height: 60%;
  top: 10%;
  transform: translate(15%, 0%);
}

form input, textarea{
    height: 10vh;
    font-family: var(--titulo);
    font-weight: 500;
    font-size: 1.2rem;
    border: none;
    border-bottom: 1px solid #000;
    border-radius: 5px;
}
</style>