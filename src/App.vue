<template>
  <div>
    <h1>Liste d'articles</h1>
    <div class="container_product">
      <product />
    </div>
  </div>
  <FooterMenu/>
</template>

<script>
import product from "./components/ProductShop";

export default {
  components: {
    product
  }
};
</script>
<style>
.container_product{
  display: flex;
  width: 80%;
  flex-wrap: wrap;
  margin: auto;
  justify-content: flex-start;
}
</style>