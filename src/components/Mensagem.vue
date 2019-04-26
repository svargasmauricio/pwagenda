<template>
  <v-form v-model="valid">
    <v-container>
      <v-layout>
        <v-flex
          xs12
          md4
        >
          <v-text-field
            v-model="firstname"
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
            v-model="lastname"
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
            v-model="email"
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
            lstServicos: [],
        }),
        created: function() {
            this.AtualizaLista();
        },
        methods: {
            EnviaMensagem(item){
                var url = this.$url_api + "/Servico/DeleteAgendaServico";

                axios({ 
                    method: "POST", 
                    "url": url, 
                    "data": JSON.stringify(item), 
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
