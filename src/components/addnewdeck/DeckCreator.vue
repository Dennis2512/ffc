<template>
  <v-col cols="12" sm="12" md="6" lg="4" xl="4">
    <v-card height="100%" raised>
      <v-card-title>Deck Creator</v-card-title>
      <v-card-text>
        <p>You will be able to natively create a new deck here.</p>
      </v-card-text>
      <div class="horizontal-spacer"></div>
      <v-card-actions class="button-padding">
        <v-spacer></v-spacer>
        <v-btn color="success" right @click="$router.push('carddeckcreator')">Create a new deck</v-btn>
      </v-card-actions>
    </v-card>
  </v-col>
</template>

<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";

@Component
export default class DeckCreator extends Vue {}
</script>

<style scoped>
#file-input-wrapper {
  padding-bottom: 0;
}
.button-padding {
  padding: 16px;
}
.v-card {
  display: flex;
  flex-direction: column;
}
.horizontal-spacer {
  flex-grow: 1;
}
</style>
