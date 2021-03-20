<template>
  <div>
    <nav>
      <router-link to="/" class="logo">
        <img src="../assets/saweblogo.svg" alt="Saweb" />
      </router-link>
      <router-link v-if="$store.state.login" class="btn" to="/usuario">{{
        nome
      }}</router-link>
      <router-link v-else class="btn" to="/login">
        Produtos / Login
      </router-link>
    </nav>
  </div>
</template>

<script>
export default {
  name: "theheader",
  computed: {
    nome() {
      return this.$store.state.usuario.nome.replace(/ .*/, "");
    },
  },
};
</script>

<style scoped>
nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 15px 20px;
  box-shadow: 0 2px 4px rgba(30, 60, 90, 0.1);
}
.logo {
  padding: 10px 0;
}
.logo img {
  width: 100px;
}
</style>