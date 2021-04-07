<template>
<div>
    <v-card class="padding" raised>
      <v-card-actions>
      <v-card-title style="cursor: pointer" @click="show = !show">Card 0</v-card-title>
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

export default class DynamicCard extends Vue {
    data() {
        return {
          show: false,
        }
    }
    deleteCard() {
      // Delete specific card and decrease the card number of following cards
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