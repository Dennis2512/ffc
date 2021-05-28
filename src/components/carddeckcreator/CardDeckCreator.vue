<template>
  <div>
    <v-container fluid style="padding-bottom: 80px">
      <!-- Display all the Cards in a seperate DynamicCard  -->
      <!-- dynamicCard defined in a different file -->
      <DeckCredentials id="deckcredentials" class="header" ref="creds" />

      <Card
        :id="index"
        v-for="(card, index) in cards"
        :key="index"
        :card="card"
        class="header"
        @delete="deleteCard(index)"
        @questionChange="onQuestionChanged($event, index)"
        @answerChange="onAnswerChanged($event, index)"
      />
    </v-container>

    <!-- Buttons that save the current Carddeck and to create a new Card -->
    <v-btn @click="saveCards" color="green" fixed right bottom
      >Save and finish</v-btn
    >
    <!-- <v-btn @click="logsmth" color="green">log</v-btn> -->
    <v-btn
      @click="addNewCard"
      fab
      elevation="2"
      dark
      color="green"
      fixed
      left
      bottom
    >
      <v-icon>mdi-plus</v-icon>
    </v-btn>
  </div>
</template>

<script>
import DeckCredentials from "./DeckCredentials.vue";
import Card from "./Card.vue";
import download from "downloadjs";
import router from "@/router";

export default {
  //the components that used in this file
  components: {
    DeckCredentials,
    Card,
  },
  data() {
    return {
      cards: [],
    };
  },

  //Methods needed in this file
  methods: {
    addNewCard() {
      //const counter = this.cards.length
      this.cards.push({
        //title: counter,
        q: "",
        a: "",
      });
    },

    saveCards() {
      if (this.$refs.creds.valid) {
        const author = this.$refs.creds.getAuthor();
        const version = this.$refs.creds.getVersion();
        const uuid = this.$refs.creds.getUUID();
        const deckname = this.$refs.creds.getDeckname();
        const description = this.$refs.creds.getDescription();
        const length = this.cards.length + 1;

        const data = {
          meta: {
            author: author,
            version: version,
            uuid: uuid,
          },
          decks: {
            d0: {
              meta: {
                deck_name: deckname,
                next_card_id: length,
                description: description,
              },
              cards: {},
            },
          },
        };

        this.cards.forEach((card, index) => (data.decks.d0.cards[index] = card));

        const object = JSON.stringify(data);
        download(object, "deck.json", object);


        router.push("/");
      }
    },
    logsmth() {
      //const data = this.cards.length
      //console.log(data);
      //const data = this.$refs.creds.getData();
      //console.log(data.author)
      const author = this.$refs.creds.getAuthor();
      const version = this.$refs.creds.getVersion();
      const uuid = this.$refs.creds.getUUID();
      const deckname = this.$refs.creds.getDeckname();
      const description = this.$refs.creds.getDescription();
      const length = this.cards.length + 1;

      const data = {
        meta: {
          author: author,
          version: version,
          uuid: uuid,
        },
        decks: {
          d0: {
            meta: {
              deck_name: deckname,
              next_card_id: length,
              description: description,
            },
            cards: {},
          },
        },
      };

      this.cards.forEach((card, index) => (data.decks.cards[index] = card));
      console.log(data);
    },

    deleteCard(index) {
      this.cards.splice(index, 1);
    },
    onQuestionChanged(question, index) {
      this.cards[index].q = question;
    },
    onAnswerChanged(answer, index) {
      this.cards[index].a = answer;
    },
  },
};
</script>

<style scoped>
.header {
  max-width: 100%;
  padding: 0;
}
</style>
