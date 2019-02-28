<template>
  <v-layout>
    <v-flex>
      <div class="imageText">
        <v-img
          :src="image.owner.src"
          :alt="image.owner.alt"
          height="250px"
          width="250px"
        />
        <h3 class="imageText-text">
          A little about us... Phasellus feugiat arcu sapien, et iaculis ipsum elementum sit amet. Mauris cursus commodo interdum. Praesent ut risus eget metus luctus accumsan id ultrices nunc. Sed at orci sed massa consectetur dignissim a sit amet dui. Duis commodo vitae velit et faucibus. Morbi vehicula lacinia malesuada. Nulla placerat augue vel ipsum ultrices, cursus iaculis dui sollicitudin. Vestibulum eu ipsum vel diam elementum tempor vel ut orci. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.
        </h3>
      </div>
      <spacer />
      <div class="imageText">
        <h3 class="imageText-text">
          What we do... Phasellus feugiat arcu sapien, et iaculis ipsum elementum sit amet. Mauris cursus commodo interdum. Praesent ut risus eget metus luctus accumsan id ultrices nunc. Sed at orci sed massa consectetur dignissim a sit amet dui. Duis commodo vitae velit et faucibus. Morbi vehicula lacinia malesuada. Nulla placerat augue vel ipsum ultrices, cursus iaculis dui sollicitudin. Vestibulum eu ipsum vel diam elementum tempor vel ut orci. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.
        </h3>
        <v-img
          :src="image.server.src"
          :alt="image.server.alt"
          height="250px"
          width="250px"
        />
      </div>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  name: 'About',
  data: () => ({
    image: {
      owner: {
        src: 'aboutImg/restaurant-owner.jpg',
        alt: 'Restaurant Owner'
      },
      server: {
        src: 'aboutImg/restaurant-server.jpg',
        alt: 'Restaurant Server'
      }
    }
  })
}
</script>

<style scoped>
    .imageText {
      display: flex;
      flex-direction: row;
      height: 50vh;
      overflow: hidden;
    }
  .imageText-text {
    padding: 25px;
    margin: 25px;
  }
</style>
