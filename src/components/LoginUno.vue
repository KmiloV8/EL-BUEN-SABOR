<template>
    <div class="main">
      <form v-on:submit.prevent="login">
  <h1 style="text-align:center; font-family:arial Black;">¡Bienvenido!</h1>
    <input
    v-model="nombreusuario"
      type="text"
      name="username"
      id="username"
      placeholder="Nombre de usuario"
      class="form-control"
      :style="input"
    />
    <br />
    <input
    v-model="password"
      type="password"
      name="password"
      id="password"
      placeholder="Contraseña"
      class="form-control"
      :style="input"
    />
    <br />
    <input @click="buscarUsuario" 
      type="submit"
      value="Iniciar Sesión"
      class="button"
      id="done"
     :style="inputStyle"
    />
  </form>
  </div>

</template>

<script>
import{ref} from 'vue'
import axios from 'axios'
import { useRouter } from 'vue-router';

export default {
  name: "LoginUno",
  //Custom style for main and input for make the page responsive:
  props: {
    mainStyle: String,
    inputStyle: String,
  },
  data(){
    return{
      //valor: this.$store.state.mostrar,
      usuarios: ref([]),
      nombreusuario: ref(""),
      password: ref(""),
      router: useRouter()
    }
  },
mounted(){
  console.log(this.valor,'valor')
},
methods:{
  buscarUsuario(){
  axios.get('https://vueinventarioaxiossa-default-rtdb.firebaseio.com/persona.json')
  .then(res=>{console.log(res);
    console.log(this.nombreusuario,'usuario')
    console.log(this.password,'usuario')

    for (const id in res.data){
      if(res.data[id].nombreusuario===this.nombreusuario && res.data[id].password ===this.password){
        console.log('ingreso')
        this.usuarios.push({
          id:id,
          nombre: res.data[id].nombre,
          password: res.data[id].password
        })
      }
    }
if (this.usuarios.length >= 1){
 /*  router.push('/Imprimir'); */
 this.$store.state.mostrar = true
 this.router.push('/');
 this.$store.state.login = false
}else{  
  alert("Usuario y contraseña incorrecto")
}
this.usuarios.value=[]
})
.catch(error => console.log(error))
  }
}
//return {nombreusuario,password,usuarios,buscarUsuario}
}
;
</script>

<style scoped>
/* Import Poppins font: */
@import url("https://fonts.googleapis.com/css2?family=Poppins&display=swap");

.main {
  background: rgba(247, 180, 45, 0.269);
  position:absolute;
  top: 20%;
  left: 35%;
  width: 30%;
  text-align: center;
  padding: 70px;
  border-radius: 3rem;
  box-shadow: 0px 0px 8px -5px #000000;
  padding-top: 3%;
  padding-bottom: 5%;
  font-family: "Poppins", sans-serif;
  display:block;
}

h1 {
  cursor: default;
  user-select: none;
  color:rgb(150, 128, 110); 
  display: flex;
}

input {
  border-radius: 3rem;
  border: none;
  padding: 10px;
  text-align: center;
  outline: none;
  margin: 10px;
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;
  font-weight: 400;
  display: flex;
}

input:hover {
  box-shadow: 0px 0px 8px -5px #000000;
}

input:active {
  box-shadow: 0px 0px 8px -5px #000000;
}

#done {
  background: rgb(135, 101, 70);
}
#done:hover{
  color:white;
  background-color: rgb(135, 101, 70);
}
.button {
  cursor: pointer;
  user-select: none;
}

img {
  height: 2.2rem;
  margin: 10px;
  user-select: none;
}

img:hover {
  box-shadow: 0px 0px 8px -5px #000000;
  cursor: pointer;
  border-radius: 200rem;
}
div{
  border: 1px solid #000000;
}
.button{
  color: white;
}

</style>
