<template>

  <v-layout
    column
    justify-center
    align-center
  >
    <!-- <v-flex
      xs12
      sm10
    > -->
    <v-text-field
          v-model="label"
          outlined
          placeholder="Rechercher..."
          clearable
          append-icon="mdi-magnify"
        ></v-text-field>
      <v-expansion-panels>
    <v-expansion-panel
      v-for="item in myFilteredData"
      :key="item.question"
    >
      <v-expansion-panel-header>{{ item.question }}</v-expansion-panel-header>
      <v-expansion-panel-content>
        {{ item.answer }}
      </v-expansion-panel-content>
    </v-expansion-panel>
  </v-expansion-panels>
      
    <!-- </v-flex> -->
  </v-layout>
</template>

<script>
import Logo from '~/components/Logo.vue'
import VuetifyLogo from '~/components/VuetifyLogo.vue'

export default {
  components: {
    Logo,
    VuetifyLogo
  },
  data: () => ({
    label: "",
    myData: [
      {   
        question: "Quel est ma couleur préférée ?",
        answer: "Ma couleur préférée est le rouge"
      },
      {
        question: "Quelle est ma chanson préférée ?",
        answer: "Ma chanson préférée est Aline de Christophe"
      }
    ]
  }),
  computed: {
    myFilteredData() {
      return this.myData.filter(item => 
        !this.label
        || (item.question.includes(this.label)) 
        || (item.answer.includes(this.label))
      )
    }
  }
}
</script>
