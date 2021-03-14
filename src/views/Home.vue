<template>
  <section>
    <h1>Indicou, Fechou, GANHOU!</h1>
    <ProdutosBuscar />
    <ProdutosLista />
  </section>
</template>

<script>
import ProdutosBuscar from '@/components/Produtos/produtosGet.vue';
import ProdutosLista from '@/components/Produtos/produtosLista.vue';

export default {
  name: 'Home',
 components:{
   ProdutosBuscar,
   ProdutosLista
 }

 
}
</script>

<style scoped>
  h1 {
    font-size: 2rem;
    color: #53bca6;
    margin-top: 40px;
    text-align: center;
  }

</style>