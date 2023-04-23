
<template>
  <label for="">Filtrer:</label>
  <select v-model="selectedCategory">
    <option value="all"> Toutes les catégories</option>
    <option value="men's clothing">men's clothing</option>
    <option value="jewelery">jewelery</option>
    <option value="electronics">electronics</option>
    <option value="women's clothing">women's clothing</option>
  </select>
  <div class="container_products">
    <v-card
        :loading="loading"
        class="mx-auto my-12 box-product"
        max-width="374"
        v-for="product in filteredProducts" :key="product.id"
    >
      <template v-slot:loader="{ isActive }">
        <v-progress-linear
            :active="isActive"
            color="deep-purple"
            height="4"
            indeterminate
        ></v-progress-linear>
      </template>

      <v-img
          height="250"
          :src="product.image"
      ></v-img>

      <v-card-item>
        <v-card-title>{{ product.title }}</v-card-title>

        <v-card-subtitle>
          <span class="me-1">{{ product.category}}</span>

          <v-icon
              color="error"
              icon="mdi-fire-circle"
              size="small"
          ></v-icon>
        </v-card-subtitle>
      </v-card-item>

      <v-card-text>
        <v-row
            align="center"
            class="mx-0"
        >
          <v-rating
              :model-value="product.rating.rate"
              color="amber"
              density="compact"
              half-increments
              readonly
              size="small"
          ></v-rating>

          <div class="text-grey ms-4">
            {{ product.rating.rate }} ({{ product.rating.count }})
          </div>
        </v-row>

        <div class="my-4 text-subtitle-1">
          {{ product.price }} €
        </div>

        <div>{{product.description.slice(0, 150)}}... <a href="">Voir plus</a></div>
      </v-card-text>

      <v-card-actions>
        <v-btn
            style="cursor: pointer;"
            color="deep-purple-lighten-2"
            variant="text"
            @click="reserve"
        >
          ACHETER
        </v-btn>
      </v-card-actions>
    </v-card>
  </div>
</template>


<script>

export default {
  data() {
    return {
      items: [],
      show: false,
      products: [],
      selectedCategory: 'all',

    };
  },
  created() {
    fetch("https://fakestoreapi.com/products")
        .then(response => response.json())
        .then(data => (this.products = data))
        .then(data => console.log(data))
  },

  computed: {
    categories() {
      const categories = ['all'];
      for (const product of this.products) {
        if (!categories.includes(product.category)) {
          categories.push(product.category);
        }
      }
      return categories;
    },
    filteredProducts() {
      if (this.selectedCategory === 'all') {
        return this.products;
      }
      return this.products.filter(product => product.category === this.selectedCategory);
    },
  },
};
</script>

<style>
.box-product{
  width: 100%;
  margin-bottom: 50px;
  z-index: -1;
}
.container_products{
  display: flex;
  flex-wrap: wrap;
}
label{
  margin-right: 10px;
}
</style>
