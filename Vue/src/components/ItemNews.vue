<template>
  <li >{{obje.title}}
    <hr>
    {{obje.url}}
  </li>
</template>

<script>
  //
  export default {
    name: "ItemNews",
    props: {
      obje: {
        type: Object,
        required: true
      }
    }
  }
</script>

<style scoped>
  li { /* Размеры */
    background: #ffcc00; /* Цвет фона */
    outline: 2px solid #000; /* Чёрная рамка */
    border: 3px solid #fff; /* Белая рамка */
    border-radius: 10px; /* Радиус скругления */
  }
</style>