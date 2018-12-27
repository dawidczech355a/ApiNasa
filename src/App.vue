<template>
  <div class="app">
    <Home />
  </div>
</template>

<script>
    import Home from '@/views/Home.vue';
    export default {
      components: {
        Home,
      }
    };
</script>

<style lang="scss">
  * {
    box-sizing: border-box;
  }
  body {
    margin: 0;
    padding: 0;
  }
</style>
