<template>
  <div class="search container d-flex">
    <div class="form-group flex-grow-1 me-2">
      <input
        type="email"
        class="form-control"
        id="exampleInputEmail1"
        aria-describedby="emailHelp"
        placeholder="Inizia la ricerca"
        v-model="searchWord"
      />
    </div>
    <button class="btn btn-primary me-2" @click="$emit('searchClicked', searchWord)">
      Cerca
    </button>
     <!-- <button class="btn btn-primary me-2" @click="sendEvent()">
      Cerca
    </button> -->
    <button class="btn btn-warning" @click="resetSearch">Reset</button>
  </div>
</template>

<script>
export default {
  name: "AppSearch",
  data: function () {
    return {
      searchWord: "",
    };
  },
  methods: {
    // sendEvent() {
    //   // Fare varie operazioni
    //   this.$emit("searchClicked", this.searchWord);
    // }
    resetSearch: function() {
      this.searchWord = "";
      this.$emit("resetClicked");
    }
  }
};
</script>

<style>
</style>

