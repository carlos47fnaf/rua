<script>
import axios from "axios";
export default {
  data() {
    return {
      cep: "",
      endereço: {},
    };
  },
  methods: {
    async buscar() {
      const url = `https://viacep.com.br/ws/${this.cep}/json/`;
      const res = await axios.get(url);
      this.endereço = res.data;
    },
  },
};
</script>
<template>
  <main>
    <h1>Buscar Cep</h1>
    <form @submit.prevent="buscar">
      <input type="text" v-model="cep" /><button type="submit">Buscar</button>
    </form>
    <form class="end">
      <label for="estado"><input type="text" v-model="endereço.uf" /></label>
      <label for="ddd"><input type="text" v-model="endereço.ddd" /></label>
      <label for="cidade"
        ><input type="text" v-model="endereço.localidade"
      /></label>
      <label for="siafi"><input type="text" v-model="endereço.siafi" /></label>
      <label for="gia"><input type="text" v-model="endereço.gia" /></label>
      <label for="ibge"><input type="text" v-model="endereço.ibge" /></label>
      <label for="bairo"></label
      ><input type="text" v-model="endereço.bairro" /> <label for="rua"></label
      ><input type="text" v-model="endereço.logradouro" />
      <label for="num"></label><input type="text" v-model="endereço.numero" />
    </form>
  </main>
  {{ endereço }}
</template>
<style scoped>
.end {
  display: flex;
  flex-direction: column;
  border: 3px black solid;
  align-items: center;
  width: 25rem;
  height: 15rem;
  text-align: center;
}
</style>
