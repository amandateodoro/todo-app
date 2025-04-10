<template>
    <div>
        <h1>Lista de Tarefas</h1>
        <table>
            <tr>
                <th>#</th>
                <th>Id</th>
                <th>Descrição</th>
                <th>Feito?</th>
            </tr>

            <tr v-for="(item, index) in tarefas" :key="index">
                <td>{{ index }}</td>
                <td>{{ item.id }}</td>
                <td>{{ item.descricao }}</td>
                <td>{{ item.feito ? 'Sim' : 'Não' }}</td>
            </tr>
        </table>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
    props: {},
    data() {
        return {
            tarefas: [
                {
                    id: 1,
                    descricao: 'Estudar JavaScript',
                    feito: false
                },
                {
                    id: 2,
                    descricao: 'Estudar TypeSript',
                    feito: true
                },
            ]
        }
    },
})
</script>