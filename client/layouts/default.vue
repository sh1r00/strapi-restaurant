<template>
  <v-app dark>
    <VuetifyTabMenu />
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <vuetify-footer />
  </v-app>
</template>

<script>
import VuetifyTabMenu from '../components/VuetifyTabMenu'
import VuetifyFooter from '../components/VuetifyFooter'
export default {
  components: { VuetifyFooter, VuetifyTabMenu }
}
</script>
