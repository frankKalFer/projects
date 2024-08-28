<template>
    <form @submit.prevent="cadastrarTarefa">
        <div class="row">
            <div class="col">
                <input :value="estado.tarefaTemp" @change="evento => estado.tarefaTemp = evento.target.value" required
                    type="text" placeholder="Digite aqui a descricao da tarefa" class="form-control">
            </div>
            <div class="col-md-2">
                <button type="submit" class="btn btn-primary">
                    Cadastrar
                </button>
            </div>
            <div class="col-md-2">
                <select @change="evento => estado.filtro = evento.target.value" class="form-control">
                    <option value="todas">Todas tarefas</option>
                    <option value="pendentes">Todas pendentes</option>
                    <option value="finalizadas">Todas finalizadas</option>
                </select>
            </div>
        </div>
    </form>
</template>