<template>
  <div>
   <ul v-if="paginaTotal > 1" class="listagem">
     <router-link :to="{query: query(1)}">
        Inicio
       </router-link>
     <li v-for="pagina in paginas" :key="pagina">
       <router-link :to="{query: query(pagina)}">
        {{pagina}}
       </router-link>
     </li>
     <router-link :to="{query: query(paginaTotal)}">
        Última
       </router-link>
   </ul>
  </div>
</template>

<script>
  export default {
    name:"produtosPaginar",

    props: {
      produtosTotal: {
        type:Number,
        default:1
      },
       produtosPorPagina: {
        type:Number,
        default:1
      }
    },
    methods:{
      query(pagina) {
        return {
          ...this.$route.query,
          _page:pagina
        }
      }
    },
    computed: {
      paginas() {
        const current = Number(this.$route.query._page);
        const range = 5;
        const offset = Math.ceil(range / 2)
        const total = this.paginaTotal;
        const pagesArray = [];

        for (let i = 1; i <= total; i++) {
          pagesArray.push(i);
        }
        pagesArray.splice(0, current - offset);
        pagesArray.splice(range, total );
        return pagesArray;
      },
      paginaTotal() {
        const total = this.produtosTotal / this.produtosPorPagina;
        return (total !== Infinity) ? Math.ceil(total) : 0;
    }
  }
  }
</script>

<style scoped>
.listagem {
  flex:1;
  display: flex;
  justify-content: flex-end;
  
}

li {
  display: inline-block;
  
}
li a {
  padding:2px 8px;
  border-radius:2px;
  margin:4px;
}

li a.router-link-exact-active,
li a:hover
 {
  background:#47a28f;
  color: #fff;
}

</style>