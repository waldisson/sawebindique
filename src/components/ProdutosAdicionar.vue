<template>
  <form class="adicionar-produto">
    <label for="nome">Nome:</label>
    <input id="nome" type="text" name="nome" v-model="produto.nome" />

    <label for="preco">Preço: (R$)</label>
    <input id="preco" type="number" name="preco" v-model="produto.preco" />

    <label for="fotos">Fotos</label>
    <input id="fotos" type="file" name="fotos" ref="fotos" />

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
      this.produto.usuario_id = this.$store.state.usuario.id;
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