<template>
  <div>
    <h3>Lista de Usuarios</h3>

    <ul class="list-group">
      <li v-for="(persona, i) in personas" :key="i"  class="list-group-item" >
        <router-link :to="`/details/${persona.id}`">{{
          persona.nombreusuario
        }}</router-link>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';
import {ref} from 'vue';
export default {
  setup(){
    const personas = ref([])
  axios.get('https://sindo-1557c-default-rtdb.firebaseio.com/persona.json')
  .then(res =>{
    console.log(res)
    for(const id in res.data){
      personas.value.push({
        id: id,
        nombreusuario: res.data[id].nombreusuario,
        password:res.data[id].password,
      })
    }
  })
  .catch(error=>console.log(error))
  return {personas};
}
  /* computed: {
    personas() {
      return this.$store.getters.getPersonas;
    },
  }, */
};
  
</script>