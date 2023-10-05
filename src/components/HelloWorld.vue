<template>
  <v-container class="fill-height">
    <v-responsive class="align-center text-center full-height">
      <v-sheet min-width="300" max-width="600" class="mx-auto">
         <div class="text-h5 font-weight-medium mb-5">
        Duhe igisokozo !
      </div>
        <v-form fast-fail @submit.prevent="sendData">
          <v-text-field
            :disabled="dialog"
            v-model="igisokozo"
            variant="outlined"
            clearable
            label="Sokozanya n'uwo muri kumwe ?"
          ></v-text-field>

          <v-textarea
            :disabled="dialog"
            v-model="inyishu"
            variant="outlined"
            clearable
            label="Izuru n'umunwa"
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
    <v-snackbar
      v-model="snackbar"
      :timeout="timeout"
      color="success"
      variant="outlined"
    >
      <v-icon slot="prependIcon" color="success" size="large" >mdi-check-circle</v-icon>
      Murakoze !
    </v-snackbar>
    <v-snackbar
      v-model="snackbar_error"
      :timeout="timeout"
      color="red"
      variant="outlined"
    >
      <v-icon slot="prependIcon" color="red" size="large" >mdi-alert-circle</v-icon>
      Uzuriza neza igisokozo cawe !
    </v-snackbar>
  </v-container>
</template>

<script>
  export default {
    data: () => ({
      /*url:"/rest_api/collect/",*/
      url:"http://127.0.0.1:8000/rest_api/collect/",
      igisokozo: "",
      snackbar:false,
      snackbar_error:false,
      dialog:false,
      timeout: 2000,
      inyishu: '',
    }),
    methods:{
      sendData(){
        if(this.inyishu.trim()?.length>3 && this.igisokozo.trim()?.length>3){
          this.loading=true
          fetch(this.url, {
            method: "POST",
            body: JSON.stringify({
              igisokozo: this.igisokozo,
              inyishu: this.inyishu
            }),
            headers: {
              "Content-type": "application/json; charset=UTF-8"
            }
          })
            .then(result => {
                //Here body is not ready yet, throw promise
                if (!result.ok) throw result;
                return result.json();
            })
            .then(result => {
                this.loading=false
                this.snackbar=true
                this.igisokozo=""
                this.inyishu=""

            }).catch((error) => {
              console.log(error)
               /* error?.json().then((body) => {
                    this.loading=false
                    console.log(body);
                });*/
            })
        }else{
          this.snackbar_error=true
        }
      }
    }
  }
</script>