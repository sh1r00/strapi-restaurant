<template>
  <div class="contact-map" />
</template>

<script>
import gmapsInit from './utils/gmaps'

export default {
  name: 'ContactsMap',
  async created() {
    try {
      const google = await gmapsInit()
      const geocoder = new google.maps.Geocoder()
      const map = new google.maps.Map(this.$el)
      // const locations = [
      //   {
      //     position: {
      //       lat: 48.160910,
      //       lng: 16.383330
      //     }
      //   }
      // ]

      geocoder.geocode({ address: 'Austria' }, (results, status) => {
        if (status !== 'OK' || !results[0]) {
          throw new Error(status)
        }
        map.setCenter(results[0].geometry.location)
        map.fitBounds(results[0].geometry.viewport)
      })

      // const markers = locations
      //  .map(x => new google.maps.Marker({...x, map}))
    } catch (error) {
      // eslint-disable-next-line
      console.error(error)
    }
  }
}
</script>

<style scoped>
    html,
    body {
        margin: 0;
        padding: 0;
    }
    .contact-map {
      height: 100%;
      width: 100%;
      padding: 20vh 15vw;
    }

</style>
