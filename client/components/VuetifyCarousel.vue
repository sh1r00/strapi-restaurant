<template>
  <v-carousel hide-controls>
    <v-carousel-item
      v-for="(item,i) in items"
      :key="i"
      :src="item.src"
    />
  </v-carousel>
</template>

<script>
export default {
  name: 'VuetifyCarousel',
  data() {
    return {
      items: [
        {
          src: 'HomeSliderImg/burger.jpg'
        },
        {
          src: 'HomeSliderImg/juice.jpg'
        },
        {
          src: 'HomeSliderImg/slushee.jpg'
        },
        {
          src: 'HomeSliderImg/pan.jpg'
        },
        {
          src: 'HomeSliderImg/wraps.jpg'
        }
      ]
    }
  }
}
</script>

<style scoped>

</style>
