<template>
  <div>
    <v-container fluid style="padding-bottom: 80px">
      <!-- Display all the Cards in a seperate DynamicCard  -->
      <!-- dynamicCard defined in a different file -->
      <DeckCredentials id="deckcredentials" class="header" ref="creds" />

      <Card
        v-for="(card, index) in cards"
        :key="card.title + index"
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
     <v-btn @click="logsmth" color="green" 
      >log</v-btn
    >
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
import DeckCredentials from './DeckCredentials.vue'
import Card from './Card.vue'
import download from 'downloadjs'
import router from '@/router'

export default {
  //the components that used in this file
  components: {
    DeckCredentials,
    Card,
  },
  data() {
    return {
      cards: [
        {
          title: 'Card 0',
          question: '',
          answer: '',
        },
        {
          title: 'Card 1',
          question: '',
          answer: '',
        },
      ],
    }
  },

  //Methods needed in this file
  methods: {
    
    addNewCard() {
      const counter = this.cards.length
      this.cards.push({
        title: 'Card ' + counter,
        question: '',
        answer: '',
      })
    },
    saveCards() {
      if (this.$refs.creds.valid) {
        const data = JSON.stringify(this.cards)
        download(data, 'deck.json', data)
        router.push("/")
      }
    },
    logsmth(){
      //const data = this.cards.length
      //console.log(data);
      const data = this.$refs.creds.getData();
      console.log(data)
    }, 

    deleteCard(index) {
      this.cards.splice(index, 1)
      // reassign Card numbers after deleting a certain one
      for( let i = 0; i < this.cards.length; i++){
          this.cards[i].title = "Card " + i
      }
    },
    onQuestionChanged(question, index) {
      this.cards[index].question = question
    },
    onAnswerChanged(answer, index) {
      this.cards[index].answer = answer
    },
  },
}
</script>

<style scoped>
.header {
  max-width: 100%;
  padding: 0;
}
</style>
