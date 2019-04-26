<template>
  <v-form v-model="valid">
    <v-container>
      <v-layout>
        <v-flex
          xs12
          md4
        >
          <v-text-field
            v-model="mensagem.nome"
            :rules="nameRules"
            :counter="10"
            label="First name"
            required
          ></v-text-field>
        </v-flex>

        <v-flex
          xs12
          md4
        >
          <v-text-field
            v-model="mensagem.sobrenome"
            :rules="nameRules"
            :counter="10"
            label="Last name"
            required
          ></v-text-field>
        </v-flex>

        <v-flex
          xs12
          md4
        >
          <v-text-field
            v-model="mensagem.email"
            :rules="emailRules"
            label="E-mail"
            required
          ></v-text-field>


        </v-flex>

        <v-flex
          xs12
          md12
        >
            <v-textarea
            v-model="mensagem.conteudo"
            name="input-7-1"
            label="Mensagem"
            hint="Hint text"
            ></v-textarea>

        </v-flex>

        <v-btn color="success" @click="EnviaMensagem">Success</v-btn>

      </v-layout>
    </v-container>
  </v-form>
</template>

<script>
    import axios from "axios";

    export default 
    {
        components: {},
        data: () => ({
            mensagem: {},
        }),
        created: function() {
            this.AtualizaLista();
        },
        methods: {
            EnviaMensagem(){
                this.mensagem.usuario = "WEB";
                var url = this.$url_api + "/Servico/EnviaMensagem";

                axios({ 
                    method: "POST", 
                    "url": url, 
                    "data": JSON.stringify(this.mensagem), 
                    "headers": { "content-type": "application/json" } 
                }).then(result => 
                {
                    this.AtualizaLista();
                }, error => {
                    console.error(error);
                });
            }
        }
    }
</script>

<style>

</style>
