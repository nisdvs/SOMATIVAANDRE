<script setup>
    const route = useRoute();
    const {data: tarefa} = await useFetch(`http://localhost:8000/tarefas/${route.params.id}`);
    const {data: tarefaUsuario} = await useFetch(`http://localhost:8000/tarefasUsuarios/?tarefa=${tarefa._rawValue.data.id}`)
    const {data: tarefaStatus} = await useFetch(`http://localhost:8000/tarefasStatus/?tarefa=${tarefa._rawValue.data.id}`)
</script>

<template>
    <div>
        <h2>
            {{ tarefa.data.id }}
        </h2>
        <h2>
            {{ tarefa.data.nome }}
        </h2>
        <h2>
            {{ tarefa.data.idStatusFK.nome }}
        </h2>
        <h2>
            {{ tarefa.data.idAmbienteFK.nome }}
        </h2>
        <h2>
            {{ tarefa.data.prazo }}
        </h2>
        <h2>
            {{ tarefa.data.dataInicio }}
        </h2>
        <h2>
            {{ tarefa.data.dataFim }}
        </h2>
        <h2>
            {{ tarefa.data.descricao }}
        </h2>
        <h2>    
            {{ tarefa.data.idSolicitanteFK.nome }}
        </h2>
        <img :src="`${tarefa.data.idSolicitanteFK.image}`">
        <hr>
            <div v-for="(tarefaUser, index) in tarefaUsuario.data" :key="index">
                <h2>
                    {{ tarefaUser.idUsuarioFK.nome }}
                </h2>
                <img :src="`${tarefaUser.idUsuarioFK.image}`">
            </div>
        <hr>
            <div v-for="(tarefaStat, index) in tarefaStatus.data" :key="index">
                <h2>
                    {{ tarefaStat.idStatusFK.nome }}
                </h2>
                <h2>
                    {{ tarefaStat.data }}
                </h2>
            </div>
    </div>
</template>