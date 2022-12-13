<template>
  <body>
    
 
  <nav class="navbar navbar-light nav-pills">
    <!-- <div class="container"> -->
      <ul class="nav">
        <li class="nav-item">
          <router-link to="/Index" class="nav-link" active-class="active"
            >Inicio</router-link
          >
        </li>
       
        <li class="nav-item" v-if="verificar">
          <router-link to="/" class="nav-link" active-class="active"
            >Agregar Usuarios</router-link
          >
        </li>
        <li class="nav-item" v-if="verificar">
          <router-link to="/print" class="nav-link" active-class="active"
            >Usuarios Registrados</router-link
          >
        </li>
         <li class="nav-item" v-if="check">
          <router-link to="/LoginUno" class="nav-link" active-class="active"
            >Inicio de Sesión</router-link
          >
        </li> 
        
        <li class="nav-item" v-if="verificar">
          <router-link to="/Pedido" class="nav-link" active-class="active"
            >¡Pedir!</router-link
          >
        </li>
        <button v-if="verificar"><a href="/log">Cerrar Sesión</a></button>
      </ul>
    <!-- </div> -->
  </nav>
</body>
</template>
<script>


export default {
 
  data(){
    return{
      error:false,
      mostrar:this.$store.state.mostrar,
      login:this.$store.state.login,
    }
  },
  computed:{
    verificar(){
    return  this.$store.state.mostrar
  },
  check(){
    return this.$store.state.login
  }
}}
</script>
<style>
body{
  background-color: rgb(248, 238, 211)
}



.nav{
  display: flex;
  justify-content: space-around;
  padding: 20px;
  background: #b57c00; /* Old browsers */
  background: -moz-linear-gradient(left, #b57c00 0%, #f7d547 100%); /* FF3.6-15 */
  background: -webkit-linear-gradient(left, #b57c00 0%,#f7d547 100%); /* Chrome10-25,Safari5.1-6 */
  background: linear-gradient(to right, #b57c00 0%,#f7d547 100%); /* W3C, IE10+, FF16+, Chrome26+, Opera12+, Safari7+ */
  filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#b57c00', endColorstr='#f7d547',GradientType=1 ); /* IE6-9 */
  text-align: center;
  width: 100%;
  
}
.nav-item{
  color: #8b6c53;
  
}
.nav-link{
  
  color: #FFF;
  background-color:#8e400000;
  border-color: #201d1a;
  transition-duration: 0.4s;
  

}
.nav-link:hover {
  background-color: #af9784;
  color: white;
}
.nav-pills .nav-link.active, .nav-pills .show>.nav-link {
    color: #fff;
    background-color: #201d1a;
    
}
.navbar{
  color:#8b6c53;
  
}
</style>
