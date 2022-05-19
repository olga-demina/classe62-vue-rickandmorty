<template>
  <section>
    <div class="main-content">
      <div v-if="loading" class="container">
        <AppLoading />
      </div>
      <div v-else class="container">
        <div class="row row-cols-2 row-cols-md-4">
          <AppCharacterCard
            v-for="item in characters"
            :key="item.id"
            :character="item"
          />
        </div>
        <div class="row">
          <AppCount :charactersNumber="characters.length"/>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import AppCharacterCard from "./AppCharacterCard.vue";
import AppLoading from "./AppLoading.vue";
import AppCount from "./AppCount.vue";
import axios from "axios";

export default {
  name: "AppCharactersList",
  components: {
    AppCharacterCard,
    AppLoading,
    AppCount,
  },
  data: function () {
    return {
      characters: [],
      loading: true,
    };
  },
  created() {
    axios
      .get("https://api.sampleapis.com/rickandmorty/characters")
      .then((resp) => {
        this.characters = resp.data;
        this.loading = false;
      });
  },
};
</script>

<style lang="scss" scoped>
</style>