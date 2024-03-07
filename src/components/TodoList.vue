<script setup>
    const props = defineProps(['tarefas']);
</script>

<template>
    <ul  class="list-group mt-4 mb-2">
        <li class="list-group-item" v-for="(tarefa, index) in props.tarefas" :key="index">
            <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada"
                :id="tarefa.titulo" type="checkbox">
            <label :class="{ done: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">
                {{ tarefa.titulo }}
            </label>
        </li>
    </ul>
    <span class="mt-5" v-if="props.tarefas.filter(tarefas => !tarefas.finalizada).length === 0">Você não possui tarefas pendentes</span>
</template>

<style scoped>
.done{
    text-decoration: line-through;
}
</style>