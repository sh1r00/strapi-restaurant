<template>
  <v-layout justify-center>
    <v-flex xs12 sm6>
      <v-toolbar color="indigo" dark>
        <v-toolbar-title>
          <h1>
            Dishes
          </h1>
        </v-toolbar-title>
        <v-spacer />
        <v-spacer />
      </v-toolbar>

      <v-card>
        <v-container
          fluid
          grid-list-md
        >
          <v-flex
            v-for="dish in dishes"
            :key="dish.id"
          >
            <v-layout row wrap>
              <v-flex>
                <v-img
                  :src="dish.image.url"
                  alt="Card image cap"
                  max-height="100px"
                  max-width="100px"
                />
              </v-flex>
              <v-flex>
                <v-card-title class="dish-details">
                  <div>
                    <div class="headline">
                      {{ dish.name }}
                    </div>
                    <div>{{ dish.description || 'No description provided' }}.</div>
                    <div>${{ dish.price }}</div>
                  </div>
                </v-card-title>
              </v-flex>
            </v-layout>
          </v-flex>
        </v-container>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
import Strapi from 'strapi-sdk-javascript/build/main'
const apiUrl = process.env.API_URL || 'http://localhost:1337'
const strapi = new Strapi(apiUrl)

export default {
  name: 'Id',
  computed: {
    id() {
      return this.$route.params.id
    },
    dishes() {
      return this.$store.getters['dishes/list']
    }
  },
  async fetch({ store, params }) {
    store.commit('dishes/emptyList')
    const response = await strapi.request('post', '/graphql', {
      data: {
        query: `query{
                    menu(id: "${params.id}") {
                        _id
                        name
                        dishes {
                            _id
                            name
                            description
                            price
                            image {
                                url
                            }
                        }
                    }
                }
                `
      }
    })
    response.data.menu.dishes.forEach((dish) => {
      dish.image.url = `${apiUrl}${dish.image.url}`
      store.commit('dishes/add', {
        id: dish._id,
        ...dish
      })
    })
  }
}
</script>

<style scoped>

</style>
