<template>
  <div>
    <h3>Registrar Usuarios</h3>
    <div class="card">
      <div class="card-body">
        <h5 class="card-title">¡Registrar Nuevo Usuario!</h5>

        <div class="form-group">
          <label for="formGroupExampleInput">Nombre</label>
          <input
            v-model="nombreusuario"
            type="text"
            class="form-control"
            placeholder="Nombre de Usuario"
          />
        </div>
        <div class="form-group">
          <label for="formGroupExampleInput2">Contraseña</label>
          <input
            v-model="password"
            type="password"
            class="form-control"
            placeholder="Contraseña"
          />
        </div>
        <!-- <div class="form-group">
          <label for="formGroupExampleInput2">Aporta</label>
          <input
            v-model="aporte"
            type="text"
            class="form-control"
            placeholder="cer-ve-za ?"
          /> 
        </div>-->
        <button class="btn btn-primary" @click="addPersona">
          A&ntilde;adir
        </button>
      </div>
    </div>
  </div>
</template>


<script>
/*eslint-disable*/
import {ref} from 'vue'
import axios from 'axios'
import {useStore} from 'vuex'
import {useRouter} from 'vue-router'
export default {
  setup(){
    const store = useStore()
    const router = useRouter()
    const nombreusuario = ref("")
    const password = ref("")
    //const aporte = ref("")

    function addPersona(){
      if(nombreusuario.value != '' && password.value != ""){
        const persona = {
          nombreusuario:nombreusuario.value,
          password:password.value
          /*aporte:aporte.value*/
        }
        /*    store.dispatch("addPersona", persona);        
        router.push('/print') */
        axios.post('https://sindo-1557c-default-rtdb.firebaseio.com/persona.json',persona).then(res=>console.log(res)).catch(error => console.log(error))
      }
    }
    return{nombreusuario, password , addPersona}
  }
  /*data() {
     return {
       nombre: "",
       email: "",
       aporte: "",
     };
   },
   methods: {
     addPersona() {
       if (this.nombre != "" && this.email != "") {
         const persona = {
           nombre: this.nombre,
           email: this.email,
           aporte: this.aporte,
         };
         this.$store.dispatch("addPersona", persona);
         this.$router.push('/print')
       }
     },
   },*/
};
</script>
<style scoped>




.main[data-v-04b5aa7d] {
    background: rgba(178, 135, 98, 0.269);
    position: absolute;
    top: 20%;
    left: 30%;
    width: 30%;
    text-align: center;
    padding: 70px;
    border-radius: 3rem
rem
;
    box-shadow: 0px 0px 8px -5px #000000;
    padding-top: 3%;
    padding-bottom: 5%;
    font-family: "Poppins", sans-serif;
    display: flex;
}
.card-body{
  text-align: center;
  padding: 40px;
  margin-top: 20px;
  align-content: center;
}
div{
  align-content: center;
  display:fixed;
  left:400px;
  border-radius: 30px;  
}
.card{
  
  
  padding: 1px;
  width: 500px;
  background-color: rgba(247, 180, 45, 0.269);
}
h3{
  text-align: center;
  
}
.btn-primary {
    color: #fff;
    background-color: #7b6134;
    border-color: #523918;
}
.form-control {
    display: block;
    width: 100%;
    height: calc(1.5em + 0.75rem + 2px);
    padding: 0.375rem 0.75rem;
    font-size: 1rem;
    font-weight: 400;
    line-height: 1.5;
    color: #495057;
    background-color: #fff;
    background-clip: padding-box;
    border: 1px solid #ced4da;
    border-radius: 20px;
    transition: border-color .15s ease-in-out,box-shadow .15s ease-in-out;
    font-family: "Poppins", sans-serif;
}
h5{
  font-family: arial black;
  font-size: 40px;
  color:#222;
  text-align: center;
}


</style>