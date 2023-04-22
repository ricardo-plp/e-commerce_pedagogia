<template>
  <v-card
      class="mx-auto box-product"
      max-width="344"
      v-for="item in items" :key="item.id"
  >
    <v-img
        :src="item.image"
        height="200px"
        coverweb
    ></v-img>

    <v-card-title>
      {{ item.title }}
    </v-card-title>

    <v-card-subtitle>
      1,000 miles of wonder
    </v-card-subtitle>

    <v-card-actions>
      <v-btn
          color="orange-lighten-2"
          variant="text"

      >
        Acheter
      </v-btn>

      <v-spacer></v-spacer>

      <v-btn
          :icon="show ? 'mdi-chevron-up' : 'mdi-chevron-down'"
          @click="show = !show"
      ></v-btn>
    </v-card-actions>

    <v-expand-transition>
      <div v-show="show">
        <v-divider></v-divider>

        <v-card-text>
          description
        </v-card-text>
      </div>
    </v-expand-transition>
    <br><br>
  </v-card>

</template>

<script>
export default {
  data() {
    return {
      items: []
    };
  },
  created() {
    fetch("https://fakestoreapi.com/products")
        .then(response => response.json())
        .then(data => (this.items = data))
        .then(data => console.log(data))
  }
};
</script>

<style>
.box-product{
  width: 100%;
  margin-bottom: 50px;
}
</style>
