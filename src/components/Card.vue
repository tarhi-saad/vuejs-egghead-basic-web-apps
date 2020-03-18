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
    title: "My title",
    content: "My <strong>awesome</strong> content is <em>on line</em>"
  })
};
</script>

<style>
</style>
