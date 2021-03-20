<template>
  <form>
    <label for="nome">Nome<span>*</span></label>
    <input id="nome" name="nome" type="text" v-model="nome" />

    <label for="email">Email<span>*</span></label>
    <input id="email" name="email" type="email" v-model="email" />

    <label for="telefone">Telefone<span>*</span></label>
    <input id="telefone" name="telefone" type="text" v-model="telefone" />

    <label for="senha">Senha<span>*</span></label>
    <input id="senha" name="senha" type="password" v-model="password" />

    <div class="button">
      <slot></slot>
    </div>
  </form>
</template>

<script>
import { mapFields } from "../../util/helpers";

export default {
  computed: {
    ...mapFields({
      fields: ["nome", "email", "telefone", "password"],
      base: "usuario",
      mutation: "UPDATE_USUARIO",
    }),
  },
};
</script>

<style scoped>
form {
  display: grid;
}
label {
  margin-top: 10px;
  margin-bottom: 5px;
}
span {
  color: red;
}
.button {
  margin-top: 20px;
}
</style>