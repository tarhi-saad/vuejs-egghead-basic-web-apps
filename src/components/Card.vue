<template>
  <v-card width="auto" class="mx-auto mt-5">
    <!-- <v-card-title>{{ title }}</v-card-title> -->
    <v-list>
      <v-subheader>{{ title }}</v-subheader>
      <v-form @submit.prevent="addItem">
        <v-text-field v-model="textInput" class="mx-4" label="Add item" prepend-inner-icon="add"></v-text-field>
      </v-form>
      <v-list-item-group color="primary">
        <v-slide-y-transition group tag="v-list">
          <v-list-item v-for="(item, index) in items" :key="item.text">
            <v-list-item-content>
              <v-list-item-title>{{ item.text }}</v-list-item-title>
            </v-list-item-content>
            <v-list-item-action>
              <v-btn icon>
                <v-icon @click="removeItem(index)" color="deep-orange darken-1">delete</v-icon>
              </v-btn>
            </v-list-item-action>
          </v-list-item>
        </v-slide-y-transition>
      </v-list-item-group>
    </v-list>
  </v-card>
</template>

<script>
export default {
  name: "Card",
  data: () => ({
    title: "Dinosaurs",
    items: [
      { text: "Frilled dragon" },
      { text: "African wild cat" },
      { text: "Malabar squirrel" },
      { text: "Sugar glider" },
      { text: "White-necked raven" }
    ],
    textInput: ""
  }),
  methods: {
    addItem() {
      if (!this.textInput) return;
      this.items.push({
        text: this.textInput
      });
      this.textInput = "";
    },
    removeItem(index) {
      this.items.splice(index, 1);
    }
  }
};
</script>

<style>
</style>
