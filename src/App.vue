<template>
  <div>
    <fieldset class="fundo">
      <h1 class="title">Reais para Dólares</h1>

      <div class="div-conversor">
        <span class="p-float-label">
          <InputText
            id="input-real"
            type="number"
            v-model="real"
            :disabled="dolars"
          />
          <label for="input-real">Quantidade em Reais</label>
        </span>
      </div>

      <div class="div-conversor">
        <span class="p-float-label">
          <InputText
            id="input-dolar"
            type="text"
            v-model="dolarCotation"
            :disabled="dolars"
          />
          <label for="input-real">Cotação do Dólar</label>
        </span>
      </div>

      <div class="div-conversor">
        <Button style="margin: 0 7px" label="Calcular" @click="calculate" />
        <Button label="Limpar" @click="clear" />
      </div>
    </fieldset>

    <div v-if="dolars">
      <p class="label-result">
        Com {{ real }} reais é possível comprar {{ dolars }} dólares a
        {{ dolarCotation }} cada
      </p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      real: '0',
      dolarCotation: 5.35,
      dolars: null,
    };
  },
  methods: {
    calculate: function() {
      this.dolars = (this.real / this.dolarCotation).toFixed(2);
    },
    clear() {
      this.real = null;
      this.dolars = null;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  color: #2c3e50;
}
.div-conversor {
  margin-top: 4rem;
  margin-left: 43%;
  justify-content: center;
}
.label-result {
  text-align: center;
  font-size: 2rem;
}
.title {
  text-align: center;
}
.fundo {
  background-color: rgba(74, 116, 170, 0.178);
}
.p-float-label {
  display: inline-block !important;
}
</style>
