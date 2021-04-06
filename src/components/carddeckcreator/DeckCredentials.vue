<template>
  <v-col cols="12" sm="12" md="6" lg="6" xl="6">
    <v-card raised>
      <v-card-title>Credentials</v-card-title>
      <v-card-text>
        <p>Please enter your credentials. These are mendatory.</p>
      </v-card-text>
      <div class="horizontal-spacer"></div>
        <v-container>
          <v-row>
            <v-col cols="12" sm="3">
              <v-text-field label="Author(s)" placeholder="John Doe" color="green" outlined clearable required></v-text-field>
            </v-col>
            <v-col cols="12" sm="2">
              <v-text-field label="Version" placeholder="1.0" color="green" outlined clearable></v-text-field>
            </v-col>
            <v-col cols="12" sm="3">
              <v-text-field label="CardDeck UUID" hint="optional" color="blue" outlined clearable></v-text-field>
            </v-col>
            <v-col cols="12" sm="4">
              <v-text-field label="CardDeck Name" placeholder="FFC Deck" color="green" outlined clearable></v-text-field>
            </v-col>
          </v-row>
          <v-row>
            <v-col cols="12" sm="12">
              <v-text-field label="CardDeck Description" placeholder="This CardDeck is for educational purpose." color="green" outlined clearable></v-text-field>
            </v-col>
          </v-row>
        </v-container>
    </v-card>
  </v-col>
</template>

<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";

@Component({})

export default class Credentials extends Vue {}
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
</style>