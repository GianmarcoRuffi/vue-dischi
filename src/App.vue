<template>
  <div id="app">
    <Header />
    <MainContent />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import MainContent from "./components/MainContent.vue";
export default {
  name: "App",
  components: {
    Header,
    MainContent,
  },
};
</script>

<style lang="scss">
@import "@/assets/general.scss";
@import "@/assets/vars.scss";
</style>
