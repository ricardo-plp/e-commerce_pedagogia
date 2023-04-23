<template>
  <v-card>
    <v-layout>

      <v-app-bar
          color="primary"
          prominent
      >

        <v-toolbar-title>E-commerce Pedagogia</v-toolbar-title>

        <v-spacer></v-spacer>

      </v-app-bar>

      <v-navigation-drawer
          v-model="drawer"
          location="bottom"
          temporary
      >
        <v-list
            :items="items"
        ></v-list>
      </v-navigation-drawer>

    </v-layout>
  </v-card>
</template>

<script>
export default {
  data: () => ({
    drawer: false,
    group: null,
    items: [
      {
        title: 'Foo',
        value: 'foo',
      },
      {
        title: 'Bar',
        value: 'bar',
      },
      {
        title: 'Fizz',
        value: 'fizz',
      },
      {
        title: 'Buzz',
        value: 'buzz',
      },
    ],
  }),

  watch: {
    group () {
      this.drawer = false
    },
  },
}
</script>

<style scoped>

</style>