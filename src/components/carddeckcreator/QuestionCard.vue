<template>
  <v-col cols="12" sm="12" md="6" lg="6" xl="6">
    <v-card class="color" height="100%" raised>
      <v-card-title>Question (front side)</v-card-title>
      <v-card-text>
        <p>Please enter your question. This will be the front of your card.</p>
      </v-card-text>
      <div class="horizontal-spacer"></div>
      <div class="container">
        <TextEditor/>
      </div>
      <!--
      <div class="horizontal-spacer"></div>
      <v-card-actions class="button-padding">
        <v-spacer></v-spacer>
        <v-btn color="red" @click="clearTextfield" right>Clear Textfield</v-btn>
      </v-card-actions>
      -->
    </v-card>
  </v-col>
</template>

<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";

import TextEditor from "./TextEditor.vue";

@Component({
  components: {
    TextEditor
  }
})
export default class QuestionCard extends Vue {}
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
.color {
  background: #282828;
}
</style>