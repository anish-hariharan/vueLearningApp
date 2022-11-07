<template>
  <the-header title="Welcome Students"></the-header>
  <the-reources></the-reources>
</template>

<script>
import TheReources from './components/learningResources/TheReources.vue';

export default {
  components: {
    TheReources,
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>
