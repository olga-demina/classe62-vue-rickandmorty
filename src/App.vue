<template>
  <div id="app">
    <AppHeader />

    <main>
      <AppCharactersList />
    </main>
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppCharactersList from "./components/AppCharactersList.vue";

export default {
  name: "App",
  components: {
    AppHeader,
    AppCharactersList
  },
};
</script>

<style lang="scss">
@import "./style/common.scss";
</style>
