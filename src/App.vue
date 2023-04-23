<template>
  <div>
    <NavBar/>
    <div class="container_product">
      <ProductShop/>
    </div>

  </div>

</template>

<script>


import ProductShop from "@/components/ProductShop";
import NavBar from "@/components/NavBar";
export default {
  components: {

    ProductShop,
    NavBar

  }
};
</script>
<style>
.container_product {
  display: flex;
  width: 90%;
  flex-wrap: wrap;
  margin: auto;
  justify-content: flex-start;
  padding-top: 100px;
}
</style>