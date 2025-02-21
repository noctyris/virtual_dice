<script>
  export default {
    props: [
      'num',
      'isLatest'
    ]
  }
</script>

<template>
  <img :src="`/images/dice${num}.svg`" :id="isLatest ? 'latest' : 'old'" :alt="`Résultat du dé: ${num}`">
</template>

<style scoped>
img {
  width: 15%;
  border: 2px solid var(--color-border);
  border-radius: 10%;
  transition: .5s;
}
img:hover {
  border: 2px solid var(--color-border-hover);
}
#latest {
  width: 25%;
}
</style>
