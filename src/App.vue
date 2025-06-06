<template>
  <div id="app">
    <TitleGenerator />
  </div>
</template>

<script>
import TitleGenerator from './components/TitleGenerator.vue';

export default {
  name: 'App',
  components: {
    TitleGenerator
  }
};
</script>


<style>
#app {
  margin: 0;
  padding: 0;
  min-height: 100vh;
  background: 
    radial-gradient(#e5e7eb 1px, transparent 1px),
    linear-gradient(to bottom right, #f9fafb, #f3f4f6);
  background-size: 20px 20px, cover;
  background-position: center;
}

</style>
