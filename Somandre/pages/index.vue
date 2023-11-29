<script setup>
definePageMeta({
    layout: "login"
})
const route = useRoute();
console.log("route", route);

const {data:usuarios} = useFetch('http://localhost:8000/usuarios/');

let botao = useState('botao', () => '');

</script>

<template>
  <div>
    <h1>Bem Vindo ao Sistema!!</h1>
    <img src="https://www.blogs.unicamp.br/ensinogeo/wp-content/uploads/sites/36/2017/02/AVA-600x381.gif">
    <br>
    <br>
    <h1>Login:</h1>
    <h4>E-mail</h4>
    <select v-model="botao">
      <option value="" disabled>Selecione um e-mail</option>
      <option v-for="(usuario,index) in usuarios.data" :key="index" :value="usuario.email">
        {{ usuario.email }}
      </option>
    </select>
    <br><br>
    <div v-if="botao!=''">
        <NuxtLink to="./homepage"><button>Oi</button></NuxtLink>
    </div>
  </div>
</template>
