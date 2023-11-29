<script setup>
const {data: tarefas} = await useFetch('http://localhost:8000/tarefas')
</script>


 
<template>
    <div>
        <div>
        <h1>
            Lista de Tarefas:
        </h1>
        <div v-for="(tareReceived,index) in tarefas.data"
        :key="index">
        <h2>
            {{tareReceived.idTarefaFK.nome}}
        </h2>
        <h2>
            {{ tareReceived.idTarefaFK.prazo }}
        </h2>
        <h2>
            {{ tareReceived.idTarefaFK.idAmbienteFK.nome }}
        </h2>
        <NuxtLink :to="`/tarefas/${tareReceived.idTarefaFK.id}`">
            <button>j</button>
        </NuxtLink >
        </div>
        </div> 

    </div>
</template>