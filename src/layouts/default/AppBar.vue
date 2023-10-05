<template>
  <v-card
    flat
    rounded="0"
    color="white"
  >
    <v-toolbar
    color="white"
    >
      <v-icon style="margin-left:10px;" color="pink" size="large">mdi-circle-slice-4</v-icon>

      <v-toolbar-title>RundiDev</v-toolbar-title>

      <v-spacer></v-spacer>
      <v-btn icon>
        <v-icon color="pink" size="large" @click.stop="dialog = true" >mdi-information</v-icon>
      </v-btn>
    </v-toolbar>
  </v-card>
  <v-dialog
      v-model="dialog"
      max-width="290"
    >
      <v-card>
        <v-card-title class="text-h6">
          Kubera iki ?
        </v-card-title>

        <v-card-text>
          Turiko dukora application ya jeux y'ibisokozo, kubwivyo turakeneye ko uduha ibisokozo uzi kugira application izobe ifise ibisokozo vyinshi kandi bitandukanye
        </v-card-text>

        <v-card-title class="text-h6">
          Utanga ibisokozo gute ?
        </v-card-title>

         <v-card-text>
          Muri formulaire yambere uzuriza igisokozo nyezina
          Hanyuma muri fomrulaire yakabiri uzuriza inyishu
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="pink"
            text
            @click="dialog = false"
          >
            Ugara
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
</template>
<script>
  export default {
    data () {
      return {
        dialog: false,
      }
    },
  }
</script>