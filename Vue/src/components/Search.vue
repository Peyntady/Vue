<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model = "city">
    <button type="submit">Search city</button>
  </form>
</template>

<script>
  export default {
    data() {
      return {
        city: ''
      }
    },
    name: "Search",
    methods: {
      onSubmit(){
        if(this.city.trim()){
          this.$emit('search', this.city);
          this.city = '';
        }
      }
    }
  }
</script>

<style scoped>
</style>