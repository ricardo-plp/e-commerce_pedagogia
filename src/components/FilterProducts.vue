<template>
  <select v-model="selectedCategory">
    <option value="all">Toutes les catégories</option>
    <option value="men's clothing">men's clothing</option>
    <option value="jewelery">jewelery</option>
    <option value="electronics">electronics</option>
    <option value="women's clothing">women's clothing</option>
  </select>
</template>

<script>
export default {
  name: "FilterProducts",
  data() {
    return {
      selectedCategory: 'all',

    };

  },
}
</script>

<style scoped>

</style>