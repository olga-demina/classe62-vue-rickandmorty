<template>
  <section>
    <AppSearch
      @searchClicked="saveSearchKey($event)"
      @resetClicked="resetSearchKey"
    />
    <div class="main-content">
      <div v-if="loading" class="container">
        <AppLoading />
      </div>
      <div v-else class="container">
        <div class="row row-cols-2 row-cols-md-4">
          <AppCharacterCard
            v-for="item in filterCharacters"
            :key="item.id"
            :character="item"
          />
        </div>
        <div class="row">
          <AppCount :charactersNumber="filterCharacters.length" />
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import AppCharacterCard from "./AppCharacterCard.vue";
import AppLoading from "./AppLoading.vue";
import AppCount from "./AppCount.vue";
import AppSearch from "./AppSearch.vue";
import axios from "axios";

export default {
  name: "AppCharactersList",
  components: {
    AppCharacterCard,
    AppLoading,
    AppCount,
    AppSearch,
  },
  data: function () {
    return {
      characters: [],
      loading: true,
      search: "",
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
  computed: {
    filterCharacters: function () {
      const keyFormatted = this.search.toLowerCase();
      const filteredCharacters = this.characters.filter((item) => {
        return item.name.toLowerCase().includes(keyFormatted);
      });
      return filteredCharacters;
    },
  },
  methods: {
    saveSearchKey: function (searchKey) {
      this.search = searchKey;
    },
    resetSearchKey() {
      this.search = "";
    },
  },
};
</script>

<style lang="scss" scoped>
</style>