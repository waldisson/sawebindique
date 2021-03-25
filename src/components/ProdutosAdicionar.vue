<template>
  <form class="adicionar-produto">
    <label for="nome">Nome:</label>
    <input type="text" name="nome" id="nome" v-model="produto.nome" />
    <label for="nome">Preço: (R$)</label>
    <input type="number" name="preco" id="preco" v-model="produto.preco" />
    <label for="nome">Fotos</label>
    <input type="file" name="fotos" id="fotos" ref="fotos" />
    <label for="nome">Descrição</label>
    <textarea
      name="descricao"
      id="descricao"
      v-model="produto.descricao"
    ></textarea>
    <input
      type="button"
      value="Adicionar Produto"
      class="btn"
      @click.prevent="adicionarProduto"
    />
  </form>
</template>

<script>
import { api } from "../services/index";

export default {
  name: "ProdutosAdicionar",

  data() {
    return {
      produto: {
        nome: "",
        preco: "",
        descricao: "",
        fotos: null,
      },
    };
  },
  methods: {
    formatarProdutos() {
      this.produto.usuario_id = this.$store.state.usuario_id;
    },
    adicionarProduto() {
      this.formatarProdutos();
      api.post("/produto", this.produto).then(() => {
        console.log(this.$store.dispatch("getUsuarioProdutos"));
      });
    },
  },
};
</script>

<style scoped>
.adicionar-produto {
  display: grid;
  grid-template-columns: 100px 1fr;
  align-items: center;
  margin-bottom: 60px;
}
input {
  margin-bottom: 10px;
}
.btn {
  grid-column: 2;
  margin-top: 10px;
}
</style>