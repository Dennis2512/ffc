<template>
<div>
  <!-- Definition of the single Cardview -->
    <v-card class="padding" raised>
      <v-card-actions>
        <!-- Title of the Card: normaly -> Card x. !-->
        <!-- The function to toggle the full Card view is implemented here -->
      <v-card-title style="cursor: pointer" @click="show = !show">{{
          card.title
        }}</v-card-title>
      <v-btn icon @click="show = !show">
        <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
      </v-btn>
      <v-spacer></v-spacer>
      <v-btn icon @click="deleteCard">
        <v-icon color="red">mdi-delete</v-icon>
      </v-btn>
      </v-card-actions>
      <v-expand-transition>
      <div v-show="show">
      <v-divider></v-divider>
      <div>
        <v-container fluid>
        <!-- Markdown Editors -->
        <v-row>
            <QuestionCard/>
            <AnswerCard/>
        </v-row>
        </v-container>
      </div>
      </div>
      </v-expand-transition>
    </v-card>
</div>
</template>

<script lang="ts">
import QuestionCard from "./QuestionCard.vue";
import AnswerCard from "./AnswerCard.vue";

export default {
  // components used 
  components: {
    QuestionCard,
    AnswerCard
  },

  // needed coming into this Object
  props: {
    card: Object,
  },
  
  //data returned from this object
  data(){
    return {
      show: false,
      pc: this.card
    }
  },

  //methods used in this Vue file.
  methods: {
    deleteCard() {
      // Delete specific card and decrease the card number of following cards
      this.pc.question = "Test"
      console.log(this.pc)
    }
  }
}
</script>

<style scoped>
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
.padding {
    margin-top: 20px;
}
</style>