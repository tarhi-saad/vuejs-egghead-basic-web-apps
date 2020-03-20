<template>
  <v-card width="400" class="mx-auto mt-5">
    <v-card-title>{{ title }}</v-card-title>
    <v-card-text v-html="content"></v-card-text>
  </v-card>
</template>

<script>
export default {
  name: "Card",
  data: () => ({
    title: "Product Engineer",
    content:
      "Nullam porttitor lacus at turpis. Donec posuere metus vitae ipsum. " +
      "Aliquam non mauris. <strong>Morbi non lectus</strong>. Aliquam sit amet diam in magna bibendum " +
      "imperdiet. <em>Nullam orci pede, venenatis non, sodales sed</em>, tincidunt eu, felis."
  })
};
</script>

<style>
</style>