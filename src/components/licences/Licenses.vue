<template>
  <div>
    <v-container fluid>
      <v-row>
        <ToastUIEditorMITLicense />
      </v-row>
    </v-container>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";

import ToastUIEditorMITLicense from "./ToastUIEditorMITLicense.vue";

@Component({
  components: {
    ToastUIEditorMITLicense
  }
})
export default class Licenses extends Vue {}
</script>

<style scoped>
</style>