<script>
import livrosApi from "@/api/livros";
const LivrosApi = new LivrosApi();
export default {
  data() {
    return {
      livros: [],
      Livros: {},
    };
  },
  async created() {
    this.livros = await livrosApi.buscarTodosOsLivros();
  },
  methods: {
    async salvar() {
      if (this.livro.id) {
        await livrosApi.atualizarLivro(this.livro);
      } else {
        await livrosApi.adicionarlivros(this.livro);
      }
      this.livro = {};
      this.livros = await livrosApi.buscarTodasAsCategorias();
    },
    editar(livro) {
      Object.assign(this.livro, livro);
    },
    async excluir(livro) {
      await livrosApi.excluirLivros(livro.id);
      this.livros = await livrosApi.buscarTodosOsLivros();
    },
  },
};
</script>

<template>
    <h1>Categoria</h1>
    <hr />
    <div class="form">
      <input type="text" v-model="categoria.descricao" placeholder="Descrição" />
      <button @click="salvar">Salvar</button>
    </div>
    <hr />
    <ul>
      <li v-for="categoria in categorias" :key="categoria.id">
        <span @click="editar(categoria)">
          ({{ categoria.id }}) - {{ categoria.descricao }} -
        </span>
        <button @click="excluir(categoria)">X</button>
      </li>
    </ul>
  </template>
  
  <style></style>