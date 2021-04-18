<template>
  <div>
    <v-container fluid>
      <!-- Display all the Cards in a seperate DynamicCard  -->
      <!-- dynamicCard defined in a different file -->
      <DeckCredentials class="header"/>
      <DynamicCard v-for="(card, index) in cards" :key="index" :card="card" class="header"/>
    </v-container>

    <!-- Buttons that save the current Carddeck and to create a new Card -->
    <v-btn @click="saveCards" color="green" fixed right bottom>Save and finish</v-btn>      
    <v-btn @click="addNewCard" fab elevation="2" dark color="green" fixed left bottom>
        <v-icon>mdi-plus</v-icon>
    </v-btn>
  </div>
</template>

<script lang="ts">
import DynamicCard from "./DynamicCard.vue";
import DeckCredentials from "./DeckCredentials.vue";


export default {
  //the components that used in this file
  components: {
    DeckCredentials,
    DynamicCard
  },
  //Methods needed in this file
  methods: {
    addNewCard() {
    // Add card to deck
    console.log(this.cards)
    },
    saveCards() {
    // Save cards as deck and close page
    }
  },
  //the returndata
  data() {
    return {
      cards: [
        {
          title: "Card 1",
          question: "",
          answer: ""
        },
        {
          title: "Card 2",
          question: "",
          answer: ""
        }
      ]
    }
  }
}

</script>

<style scoped>
.header {
  max-width: 100%;
  padding: 0;
}
</style>