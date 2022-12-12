<template>
  <app-header class="mb-3" /> 

  <router-view />
  
</template>

<script>
import Header from "./components/Header";
export default {
  name: "App",
  components: {
    "app-header": Header,
    //LoginUno
  },
  data(){
    return{
      error:false,
      mostrar:this.$store.state.mostrar,
    }
  },
  computed:{
    verificar(){
    return  this.$store.state.mostrar
  }
}}
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

</style>
