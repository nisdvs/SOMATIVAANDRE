<script setup>
const {data: ambientes} = await useFetch('http://localhost:8000/ambientes',{
    key: 'reLoad'
});


let showForm = false;
    const setshowForm = () => {
        showForm = true;
        console.log("showForm", showForm)
        refreshNuxtData('reLoad') 

    }

let novoAmbiente;


const sendForm = async () => {
    await useFetch('http://localhost:8000/ambientes/', {
    method: 'POST',
    body: [{
        'nome':novoAmbiente
    }],
    onResponse() {
        refreshNuxtData('reLoad')
    },
    onResponseError() {
        alert("erro!")
    }
    })
}
</script>




<template>
    <div>
        <h1>
            Lista de Ambientes:
        </h1>
        <div v-for="(AmbiReceived,index) in ambientes.data"
        :key="index">
        <h2>
            {{ AmbiReceived.nome }}
        </h2>
    </div>
    <section>
            <div>
                <label for="">Nome:</label> <input type="text" v-model="novoAmbiente"> <br>
            </div>
            <button @click="sendForm"> Enviar</button>
        </section>
</div>
</template>