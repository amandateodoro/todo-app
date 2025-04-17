<template>
  <div class="mt-5">
    <h1>Lista de Tarefas</h1>

    <button v-if="!abrirForm" @click="abrirForm = true">Nova Tarefa</button>

    <div v-if="abrirForm">
      <form>
        <input type="text" v-model="descricao" placeholder="Informe a descrição da tarefa" />
        <button @click="adicionar">Adicionar</button>
      </form>
    </div>

    <table>
      <tr>
        <th>#</th>
        <th>Id</th>
        <th>Descrição</th>
        <th>Feito?</th>
        <th>Ação?</th>
      </tr>

      <tr v-for="(item, index) in tarefas" :key="index">
        <td>{{ index }}</td>
        <td>{{ item.id }}</td>
        <td>{{ item.descricao }}</td>
        <td>{{ item.feito ? 'Sim' : 'Não' }}</td>
        <td>
          <button @click="finalizar(item.id)">Finalizar</button>
          <button @click="excluir(item.id)">X</button>
        </td>
      </tr>
    </table>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  props: {},
  data() {
    return {
      tarefas: [
        {
          id: 1,
          descricao: 'Estudar JavaScript',
          feito: false,
        },
        {
          id: 2,
          descricao: 'Estudar TypeSript',
          feito: true,
        },
      ],
      descricao: null,
      abrirForm: false,
    }
  },

  methods: {
    adicionar() {
      const id = this.tarefas.length + 1
      if (this.descricao != null) {
        const novaTarefa = {
          id: id,
          descricao: this.descricao,
          feito: false,
        }

        this.tarefas.push(novaTarefa)
        this.descricao = null
        this.abrirForm = false
      }
    },

    excluir(id: Number) {
        const novaLista = this.tarefas.filter(item => {
            return item.id != id;
        });

        this.tarefas = novaLista;
    },

    finalizar(id: Number) {
      for (const item of this.tarefas) {
        if (item.id == id) {
          item.feito == true
        }
      }
    },
  },
})
</script>
