<script setup>
import { reactive } from "vue";
import Header from './components/Header.vue';
import Form from './components/Form.vue';
import List from './components/List.vue';

const estado = reactive({
    filtro: 'todas',
    tarefaTemp: '',
    tarefas: [
        {
            titulo: 'Estudar ES6',
            finalizada: false,
        },
        {
            titulo: 'Estudar SASS',
            finalizada: false,
        },

        {
            titulo: 'Fazer tarefa mod-8',
            finalizada: true,
        }
    ]
})

const getTarefasPendentes = () => {
    return estado.tarefas.filter(tarefa => !tarefa.finalizada)
}

const getTarefasFinalizadas = () => {
    return estado.tarefas.filter(tarefa => tarefa.finalizada)
}

const getTarefasFiltradas = () => {
    const { filtro } = estado;

    switch (filtro) {
        case 'pendentes':
            return getTarefasPendentes();
        case 'finalizadas':
            return getTarefasFinalizadas();
        default:
            return estado.tarefas;
    }
}

const cadastrarTarefa = () => {
    const tarefaNova = {
        titulo: estado.tarefaTemp,
        finalizada: false,
    }

    estado.tarefas.push(tarefaNova);
    estado.tarefaTemp = '';
}
</script>

<template>
    <div class="container">
        <Header  />
        <Form />
        <List />
    </div>
</template>

<style scoped>
.done {
    text-decoration: line-through;
}
</style>
