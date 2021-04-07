<template>
  <div>
    <v-container fluid>
      <DeckCredentials class="header"/>
      <DynamicCard class="header"/>
    </v-container>
    <v-btn @click="saveCards" color="green" fixed right bottom>Save and finish</v-btn>      
    <v-btn @click="addNewCard" fab elevation="2" dark color="green" fixed left bottom>
        <v-icon>mdi-plus</v-icon>
    </v-btn>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";

import DynamicCard from "./DynamicCard.vue";
import DeckCredentials from "./DeckCredentials.vue";

@Component({
  components: {
    DeckCredentials,
    DynamicCard
  }
})

export default class CardDeckCreator extends Vue {
  addNewCard() {
    // Add a new Card dynamically
  }
  saveCards() {
    // Save cards as deck and close page
  }
}
</script>

<style scoped>
.header {
  max-width: 100%;
  padding: 0;
}
</style>