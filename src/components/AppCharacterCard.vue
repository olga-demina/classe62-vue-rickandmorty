<template>
  <div class="character-card text-center p-3">
      <img class="rounded-circle" :src="character.image" alt="">
      <h2 class="character-name mt-3">{{ character.name }}</h2>

      <p>{{ character.origin }}</p>
      <p class="fw-bold">{{ character.type }}</p>
  </div>
</template>

<script>
export default {
    name: "AppCharacterCard",
    props: {
        character: Object
    }
}
</script>

<style lang="scss" scoped>

.character-card {
    .character-name {
        font-size: 1.4rem;

        &::after {
            content: '';
            display: block;
            width: 3rem;
            height: 2px;
            background-color: black;
            margin: 1rem auto;
        }
    }
}

</style>