<template>
  <v-container class="fill-height">
    <v-responsive class="align-center text-center full-height">

      <v-sheet min-width="300" max-width="600" class="mx-auto">
         <div class="text-h5 font-weight-medium mb-5">
        Duhe igisokozo !
      </div>
        <v-form fast-fail @submit.prevent>
          <v-text-field
            v-model="igisokozo"
            variant="outlined"
            clearable
            label="Sokozanya n'uwo muri kumwe ?"
            :rules="igisokozoRules"
          ></v-text-field>

          <v-textarea
            v-model="lastName"
            variant="outlined"
            clearable
            label="Izuru n'umunwa"
            :rules="inyishu"
          ></v-textarea>

          <v-btn
            :disabled="loading"
            :loading="loading"
            block
            type="submit"
            class="text-none mb-4 mt-2"
            color="pink"
            size="x-large"
            variant="elevated"
            @click="loading = !loading"
          >
            Rungika
          </v-btn>
        </v-form>
      </v-sheet>
    </v-responsive>
    <v-footer >
      <v-row justify="center" no-gutters>
        <v-col class="text-center mt-4" cols="12">
          {{ new Date().getFullYear() }} — <strong style="color:blue">RundiDev</strong>
          Powered by <strong><a href="https://www.ksquad.dev" target="_blank" style="text-decoration:none;color:#E91E63">K SQUAD</a></strong>
        </v-col>
      </v-row>
    </v-footer>
  </v-container>
</template>

<script>
  export default {
    data: () => ({
      igisokozo: "",
      igisokozoRules: [
        value => {
          if (value.trim()?.length > 3) return true

          return 'Shiramwo igisokozo kibaho koko !'
        },
      ],
      inyishu: '',
      inyishuRules: [
        value => {
          if (value.trim()?.length > 3) return true

          return `Utegerezwa kwuzuza inyishu y'igisokozo`
        },
      ],
    }),
  }
</script>