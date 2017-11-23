<template>
  <v-app light>
    <main app>
      <v-container grid-list-lg text-sm-center>
        <v-slide-y-transition mode="out-in">
          <v-layout column align-center>
            <v-flex class="ma-5"></v-flex>
            <v-flex class="ma-5"></v-flex>

            <v-card class="elevation-2 pl-5 pr-5 pb-3">
               <v-text-field
               box
               :label="nameLabel"
               v-model="waldonian"
               @keyup.enter="submit()"
               ></v-text-field>

               <v-btn
               @click="submit()"
               dark
               >Enter the Void</v-btn>
             </v-card>
          </v-layout>
        </v-slide-y-transition>
      </v-container>
    </main>

    <v-footer :fixed="fixed" app>
      <span>Drakkun &copy; 2017</span>
    </v-footer>
  </v-app>
</template>

<script>
  export default {
    data () {
      return {
        waldonian: '',
        fixed: true,
        nameLabel: 'Who are you?',
        title: 'Vuetify.js'
      }
    },
    beforeCreate () {
      this.$http.get('/api/').then(response => {
        console.log(response)
      }, response => {
        console.error(response)
      })
    },
    methods: {
      submit () {
        if (this.waldonian.trim() === '') {
          this.nameLabel += ' Really?'
          return
        }
        // else check with backend
      }
    }
  }
</script>
