<template>
  <v-layout row-wrap>
    <v-flex xs12 sm4>
      <v-card v-for="note in notes">
        <v-img src="https://cdn.vuetifyjs.com/images/cards/desert.jpg" aspect-ratio="2.75"></v-img>

        <v-card-title primary-title>
          <h1>ID NOTA {{note.id}}</h1>
        </v-card-title>
        <h2>CONTENIDO NOTA</h2>
        <span class="headline mb-0">{{note.text}}</span>
      </v-card>
    </v-flex>
    <v-flex xs12 sm4>
      <form>
        <v-text-field
          id="txtId"
          :counter="10"
          label="id nota"
          required
          @input="$v.name.$touch()"
          @blur="$v.name.$touch()"
        ></v-text-field>
        <v-text-field
          id="txtTexto"
          label="texto"
          required
          @input="$v.email.$touch()"
          @blur="$v.email.$touch()"
        ></v-text-field>

        <v-btn @click="postNotes()">submit</v-btn>
      </form>
    </v-flex>
  </v-layout>
</template>
<script>
var axios = require("axios");
export default {
  created() {
    this.getNotes();
    console.log("tag", this.notes);
  },
  data() {
    return {
      urlAPI:
        "https://hb70aoxp1d.execute-api.us-west-1.amazonaws.com/dev/efraUserNotes",
      notes: []
    };
  },
  methods: {
    getNotes: function() {
      var that = this;
      axios.get(this.urlAPI).then(function(response) {
        that.notes = response.data;
        console.log(response.data);
      });
    },
    postNotes: function() {
      let idd = document.getElementById("txtId").value;
      let texto = document.getElementById("txtTexto").value;
      axios
        .post(this.urlAPI, {
          id: idd,
          text: texto
        })
        .then(function(response) {
          console.log(response);
        })
        .catch(function(error) {
          console.log(error);
        });
    }
  }
};
</script>