<template>
  <h3 class="text-center">Trovati {{ charactersNumber }} personaggi</h3>
</template>

<script>
export default {
    name: "AppCount",
    props: {
        charactersNumber: Number
    }
};
</script>

<style>
</style>