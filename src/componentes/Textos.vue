<template>
  <div class="jumbotron">
    <form @submit.prevent>
      <input type="text" v-model="textoIngresado" placeholder="Ingrese un texto"/>
    </form>
    <div v-show="visibilidad()" >
      <p>1.- Cantidad de Caracteres: {{ cantCaracteres }}</p>
      <p>2.- Cantidad de Vocales: {{ cantVocales }}</p>
      <p>3.- Texto en Mayúsculas: {{ textoMayuscula }}</p>
      <p>4.- Texto Invertido: {{ textoInvertido }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
    textoIngresado: '',
    }
  },
  computed: {
    cantCaracteres() {
      return this.textoIngresado.length;
    },
    cantVocales() {
      let vocales = 0;
      for (let char of this.textoIngresado.toLowerCase()) {
        if (char === 'a' || char === 'e' || char === 'i' || char === 'o' || char === 'u') {
          vocales++;
        }
      }
      return vocales;
    },
    textoMayuscula() {
      return this.textoIngresado.toUpperCase();
    },
    textoInvertido() {
      let otxet = '';
      for (let i = this.textoIngresado.length - 1; i >= 0; i--) {
        otxet += this.textoIngresado[i];
      }
      return otxet;
    },
  },
  methods: {
    visibilidad(){
      return this.textoIngresado.length
    }
  }
}
</script>

<style scoped lang="css">
  .jumbotron{
    font-weight: bold;
  }
</style>
