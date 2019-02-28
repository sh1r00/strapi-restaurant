<template>
  <v-toolbar>
    <v-toolbar-title>
      <v-btn
        :to="url.home"
      >
        Restaurant Name
      </v-btn>
    </v-toolbar-title>
    <v-spacer />

    <v-toolbar-items>
      <v-layout
        justify-center
        row
        wrap
      >
        <v-btn
          v-for="(link,i) in links"
          :key="i"
          :to="link.address"
          color="white"
          flat
          round
        >
          {{ link.name }}
        </v-btn>
      </v-layout>
    </v-toolbar-items>
  </v-toolbar>
</template>

<script>
export default {
  name: 'VuetifyTabMenu',
  data: () => ({
    url: {
      home: '/'
    },
    links: [
      {
        icon: 'apps',
        name: 'Home',
        address: '/'
      },
      {
        name: 'About Us',
        address: '/about'
      },
      {
        name: 'Our Menu',
        address: '/menu'
      },
      {
        icon: 'bubble_chart',
        name: 'Contact Us',
        address: '/contact'
      }
    ]
  })
}
</script>

<style scoped>

</style>
