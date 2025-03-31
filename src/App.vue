<template>
  <div id="app">
    <BuscarOperadoras />
  </div>
</template>

<script>
import BuscarOperadoras from './components/BuscarOperadoras.vue';

export default {
  name: 'App',
  components: {
    BuscarOperadoras
  }
};
</script>

<style>
body {
  margin: 0;
  background: #f8f8f8;
}
</style>
