<template>
  <v-layout row wrap>
    <vuetify-carousel />
    <v-flex d-flex>
      <v-card
        :to="links.about"
        align-content-center
        height="100px"
      >
        <v-card-text>
          Get to know us
        </v-card-text>
      </v-card>
      <v-card
        :to="links.menu"
        height="100px"
      >
        <v-card-text>
          What we offer
        </v-card-text>
      </v-card>
      <v-card
        :to="links.contact"
        height="100px"
      >
        <v-card-text>
          Come find us
        </v-card-text>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>

import VuetifyCarousel from '../components/VuetifyCarousel'
export default {
  components: { VuetifyCarousel },
  data: () => ({
    links: {
      about: 'about',
      menu: 'menu',
      contact: 'contact'
    }
  })
}
</script>
