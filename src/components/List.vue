<template>
  <v-card width="auto" class="mx-auto mt-5">
    <!-- <v-card-title>{{ title }}</v-card-title> -->
    <v-list three-line>
      <v-subheader>{{ title }}</v-subheader>
      <v-form @submit.prevent="addItem">
        <v-text-field
          v-model="textInput"
          class="mx-4"
          label="Add item"
          prepend-inner-icon="add"
          autocomplete="off"
        ></v-text-field>
      </v-form>
      <v-list-item-group color="primary">
        <!-- <v-slide-y-transition group tag="v-list"> -->
        <v-list-item
          v-for="(item, index) in items"
          :key="`${index + Math.round(Math.random() * 10000)}${item.text}`"
        >
          <v-list-item-content>
            <v-list-item-title>{{ item.text | capitalize }}</v-list-item-title>
            <v-list-item-subtitle>
              The scientific name of
              <strong>{{ item.text | undercase }}</strong> is
              <strong>{{ item.scientificName | undercase }}</strong>
              <br>
              <a :href="item.text | url" :alt="item.text" target="_blank">{{ item.text | undercase | url}}</a>
            </v-list-item-subtitle>
          </v-list-item-content>
          <v-list-item-action>
            <v-btn icon>
              <v-icon @click="removeItem(index)" color="deep-orange darken-1">delete</v-icon>
            </v-btn>
          </v-list-item-action>
        </v-list-item>
        <!-- </v-slide-y-transition> -->
      </v-list-item-group>
    </v-list>
  </v-card>
</template>

<script>
import { gsap } from "gsap";

export default {
  name: "Card",
  data: () => ({
    title: "Dinosaurs",
    items: [
      {
        text: "frilled dragon",
        scientificName: "Chlamydosaurus kingii"
      },
      {
        text: "African wild cat",
        scientificName: "Felis silvestris lybica"
      },
      {
        text: "malabar squirrel",
        scientificName: "Chlamydosaurus kingii"
      },
      {
        text: "Sugar glider",
        scientificName: "Petaurus breviceps"
      },
      {
        text: "white-necked raven",
        scientificName: "Corvus albicollis"
      }
    ],
    textInput: ""
  }),
  filters: {
    capitalize(value) {
      if (!value) return "";
      const stringValue = value.toString();
      return stringValue.charAt(0).toUpperCase() + stringValue.slice(1);
    },
    undercase(value) {
      if (!value) return "";

      const stringValue = value.toString();
      return stringValue.toLowerCase();
    },
    url(value) {
      if (!value) return "";
      return `https://en.wikipedia.org/wiki/${value}`;
    }
  },
  methods: {
    addItem() {
      if (!this.textInput) return;

      const addedItem = [{ text: this.textInput }];
      const updatedItem = addedItem.concat(this.items);
      this.items = updatedItem;
      this.textInput = "";

      // Animation
      this.$nextTick(function() {
        gsap.from(".v-list .v-list-item:first-child", {
          duration: 0.5,
          opacity: 0,
          y: -60
        });
        gsap.from(".v-list .v-list-item:not(:first-child)", {
          duration: 0.5,
          y: -60
        });
        gsap.set(".v-list", { height: "auto" });
        gsap.from(".v-list", {
          duration: 0.5,
          height: "-=60"
        });
      });
    },
    removeItem(index) {
      const updatedItem = [...this.items];
      updatedItem.splice(index, 1);
      this.items = updatedItem;

      // Animation
      gsap.set(".v-list", { height: "-=0" });
      this.$nextTick(function() {
        gsap.from(`.v-list-item:nth-child(n + ${index + 1})`, {
          duration: 0.5,
          y: +60
        });
        gsap.to(".v-list", {
          duration: 0.5,
          height: "-=60"
        });
      });
    }
  }
};
</script>

<style>
</style>
