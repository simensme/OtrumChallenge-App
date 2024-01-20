<script setup>
import { RouterView } from 'vue-router';
import NameList from './components/NameList.vue';
</script>

<template>
  <NameList/>
  <RouterView />
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');
html {
  background: rgb(227, 227, 227);
  box-sizing: border-box;
}

body {
  margin: 0;
  min-height: 100vh;
  font-family: 'Roboto', sans-serif;
  display: flex;
}

</style>