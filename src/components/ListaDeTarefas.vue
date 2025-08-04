<script setup>
const props = defineProps(['tarefas']);
const mensage = false;

</script>

<template>
    <div v-if="props.tarefas.length === 0" class="alert alert-info mt-4">
        Nenhuma tarefa cadastrada!
    </div>
    <ul v-else-if="mensage === false" class="list-group mt-4">
        <li class="list-group-item" v-for="tarefa in props.tarefas">
            <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada"
                :id="tarefa.titulo" type="checkbox">
            <label class="ms-3" :class="{ done: tarefa.finalizada }" :for="tarefa.titulo">
                {{ tarefa.titulo }}
            </label>
        </li>
    </ul>
</template>

<style scoped>
:global(.done) {
    /* css global para class de seletores dinamicos */
    text-decoration: line-through;
}
</style>