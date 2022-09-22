
<template>
  <div class="login" v-if="ver_publicaciones === false" >
    <h1 class="login_title">Iniciar Sesion</h1>
    <form action="" class="login_form" v-on:submit.prevent="login">
      <input type="text" class="login_input" v-model="Nombre" required placeholder="Nombre">
      <input type="password" class="login_input" placeholder="Contraseña">
      <button type="submit" class="login_input_enviar">Enviar</button>
    </form>
  </div>

 

  
  


  <div class="menu" v-if="ver_publicaciones === true"> 
   <div class="menu_items">
    <button v-on:click="display">Ver Publicaciones</button>
    <button v-on:click="display">Crear</button>
      <button v-on:click="ver_publicaciones = false">Log out</button>
        Bienvenido  {{Nombre_login}}
  </div>
  </div>
<div class="crear">
   <div v-if="crear_pub===true" >
    <div>
       <CrearpubVue @send="escuchar"></CrearpubVue>
        
    </div>
   
  </div>
</div>
 

<div class="pub" v-if="crear_pub===false"> 
  <div class="pub_box" v-for="resultpadre of resultpadres">
    {{resultpadre.titulo}}
   
  </div>

  
</div>
  

</template>

<script>
  import PublicacionesVue from './components/Publicaciones.vue'
  import CrearpubVue from './components/Crearpub.vue'
  export default{
    name: "App",
    Publicaciones : PublicacionesVue,
    Crear : CrearpubVue,
    data() {
        return {
            ver_publicaciones: false,
            crear_pub: false,
            Nombre: "",
            Nombre_login: "",
          
            resultpadres:[],
            titulo: "",
            cuerpo:""
        };
        
    },methods:{
          login(){
            this.crear_pub = true,
            this.ver_publicaciones = true,
            this.Nombre_login = this.Nombre,
            this.Nombre = ""
          },
          display(){
            if(!this.crear_pub){
              this.crear_pub = true;
            } else{
              this.crear_pub = false;
            }
          },
          escuchar(event){
            this.results = event
            
            
            this.resultpadres.push({
              titulo : this.results,
              cuerpo: this.results
            })
          } 

        },
    components: { PublicacionesVue, CrearpubVue }
}


</script>

<style>
  *{
    z-index: 100 !important;
    overflow-x: hidden;
  }
  .login{
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100vw;
    height: 100vh;
    background-color: #2d7ff2;
    
    top: 50%;
    left: 50%;
    justify-content: center;
    transition: opacity .5s ease;
  }

  
  .login_title{
    color: #fff;
    font-family: var(--titulo);
    font-weight: bold;
  }

 .login_form{
  margin: 20px;
    display: flex;
    flex-direction: column;
    width:  50%;
  }

  input{
    margin-bottom: 15px;
    height: 50px;
    border-radius: 5px;
    outline: none;
    border-color: none;
    
  }
  input:focus, textarea:focus{
    outline: none;
    
  }
  .main_body{
  
    width: 100vw;
    background-color: aliceblue;
  }
  .menu{
    display: flex;
    flex-direction: row;
    position: absolute ;
    top: 0;
    width: 100%;   
    align-items: center;
    height: 80px;
    background-color: #2d7ff2;
    flex-flow: row-reverse;
    padding-right: 15px;
    color: #fff;
  }
  .menu_items>*{
    margin-right: 2rem;
  }
  .publicacion{
    margin-top: 80px;
    display: block;
    position: fixed;
  }
  .pub{
    margin-top: 120px;
   
width: 100vw;

display: flex;
justify-content: flex-start;
flex-direction: column;
align-items: center;

  }
.pub_box{
  width: 70%;
  background-color: rgb(255, 255, 255);
padding-left: 30px;
font-size: 1.2rem;
border: none;

border-left: 1px solid black;
border-right: 1px solid black;
}

  .pub_box:nth-child(2n-1){
    font-weight: bolder;
padding-left: 15px;  
padding-right: 15px;
padding-top: 30px;
padding-bottom: 15px;
font-size: 2rem;
border-top: 1px solid black;
} 
.pub_box:nth-child(2n){
  margin-bottom: 30px;
  padding-bottom: 15px;
  border-bottom: 1px solid black;
}
.crear{
  position: fixed;
  display: flex;
  flex-direction: column-reverse;
}
</style>
