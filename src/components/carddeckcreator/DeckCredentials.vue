<template>
  <v-col cols="12" sm="12" md="6" lg="6" xl="6">
    <v-card raised>
      <v-card-title>Credentials</v-card-title>
      <v-card-text>
        <p>Please enter your credentials. These are mendatory.</p>
      </v-card-text>
      <div class="horizontal-spacer"></div>
      <v-container>
        <v-form v-model="valid">
          <v-row>
            <v-col cols="12" sm="3">
              <v-text-field
                id="author"
                v-model="author"
                label="Author(s)"
                placeholder="John Doe"
                color="green"
                outlined
                clearable
                required
                :rules="rules"
                autocomplete="off"
              ></v-text-field>
            </v-col>
            <v-col cols="12" sm="2">
              <v-text-field
                v-model="version"
                label="Version"
                placeholder="1.0"
                color="green"
                outlined
                clearable
                :rules="rules"
                autocomplete="off"
              ></v-text-field>
            </v-col>
            <v-col cols="12" sm="3">
              <v-text-field
                v-model="uuid"
                label="CardDeck UUID"
                hint="optional"
                color="blue"
                outlined
                clearable
                autocomplete="off"
              ></v-text-field>
            </v-col>
            <v-col cols="12" sm="4">
              <v-text-field
                v-model="deckname"
                label="CardDeck Name"
                placeholder="FFC Deck"
                color="green"
                outlined
                clearable
                :rules="rules"
                autocomplete="off"
              ></v-text-field>
            </v-col>
          </v-row>
          <v-row>
            <v-col cols="12" sm="12">
              <v-text-field
                v-model="description"
                label="CardDeck Description"
                placeholder="This CardDeck is for educational purpose."
                color="green"
                outlined
                clearable
                autocomplete="false"
                :rules="rules"
              ></v-text-field>
            </v-col>
          </v-row>
        </v-form>
      </v-container>
    </v-card>
  </v-col>
</template>

<script lang="ts">
import Vue from 'vue'
import Component from 'vue-class-component'

@Component({})

export default class Credentials extends Vue {
  valid = false
  rules = [(v: string) => !!v || 'This field is required']  
  
  author = ""
  version =""
  uuid=""
  deckname=""
  description=""


  public test (){
    console.log("hi")
  }


  public getAuthor(){
    if(this.valid){
      return this.author 
    }
    else{return null}
  }

  public getVersion(){
    if(this.valid){
      return this.version
    }
      else{return null}
  }

  public getUUID(){ 
    if(this.valid){
      return this.uuid
  }else{
    return null}
  }

  public getDeckname(){
    if(this.valid){
      return this.deckname
    }else{
      return null
    }
  }

  public getDescription(){
    if(this.valid){
      return this.description
    }else{
      return null
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
</style>
