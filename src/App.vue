<template>
  <div id="app">
    <h1>Inventario de Juegos</h1>
    <JuegosComponente />
  </div>
</template>

<script>
import JuegosComponente from './components/JuegosComponente.vue';

export default {
  components: {
    JuegosComponente
  }
};
</script>
