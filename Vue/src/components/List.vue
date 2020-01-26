<template>
  <ul>
    <ItemNews
            v-for="obje of obj"
            v-bind:key="obje.id"
            v-bind:obje="obje"
    />
  </ul>
</template>

<script>
  //
  import ItemNews from "@/components/ItemNews"
  export default {
    name: "List",
    props: ['obj'],
    components: {ItemNews}
  }
</script>

<style scoped>
</style>