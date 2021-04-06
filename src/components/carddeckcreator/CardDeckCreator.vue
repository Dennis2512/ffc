<template>
  <div>
    <v-container fluid>
      <v-row>
        <QuestionCard/>
        <AnswerCard/>
      </v-row>
    </v-container>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";

import QuestionCard from "./QuestionCard.vue";
import AnswerCard from "./AnswerCard.vue";

@Component({
  components: {
    QuestionCard,
    AnswerCard
  }
})

export default class CardDeckCreator extends Vue {}
</script>

<style scoped>
</style>