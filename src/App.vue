<template>
  <div id="app">
    <router-view/>
    <footer-prismic/>
  </div>
</template>

<script>
import FooterPrismic from './components/FooterPrismic.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    FooterPrismic
  }
}
</script>

<style>
@import "./assets/css/resetr.css";
@import "./assets/css/prismic-edit-button.css";
@import "./assets/css/bootstrap.css";
@import "./assets/css/main.css";
</style>
