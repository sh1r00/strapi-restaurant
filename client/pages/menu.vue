<template>
  <v-layout justify-center>
    <v-flex xs12 sm6>
      <v-toolbar color="indigo" dark>
        <v-toolbar-title>
          <h1>
            Menu
          </h1>
        </v-toolbar-title>
        <v-spacer />
        <v-btn
          icon
          :href="url.admin"
        >
          <v-icon>fab fa-cog</v-icon>
        </v-btn>
      </v-toolbar>

      <v-card>
        <v-container
          fluid
          grid-list-md
        >
          <v-layout row wrap>
            <v-flex
              v-for="menu in filteredList"
              :key="menu.id"
            >
              <v-img
                :src="menu.image.url"
                height="200px"
              >
                <v-container
                  fill-height
                  fluid
                  pa-2
                >
                  <v-layout fill-height>
                    <v-flex sx12 align-end flexbox>
                      <span class="headline white--text"> {{ menu.name }}</span>
                    </v-flex>
                  </v-layout>
                </v-container>
              </v-img>
              <v-card-title>
                <div>
                  <span class=" grey--text">{{ menu.description || 'No desctiption provided' }}.</span>
                </div>
              </v-card-title>
              <v-card-actions>
                <v-btn
                  :to="{name:'menus-id', params:{id:menu._id}}"
                  tag="a"
                  flat
                  color="orange"
                >
                  Check out our {{ menu.name }}
                </v-btn>
              </v-card-actions>
            </v-flex>
            <p v-if="!filteredList.length">
              No results :(
            </p>
          </v-layout>
        </v-container>
      </v-card>
      <div>
        <ul />
      </div>
    </v-flex>
  </v-layout>
</template>

<script>
import Strapi from 'strapi-sdk-javascript/build/main'
const apiUrl = process.env.API_URL || 'http://localhost:1337'
const strapi = new Strapi(apiUrl)

export default {
  name: 'Menu',
  data() {
    return {
      query: '',
      url: {
        admin: apiUrl + '/admin'
      }
    }
  },
  computed: {
    filteredList() {
      return this.menus.filter((menu) => {
        return menu.name.toLowerCase().includes(this.query.toLowerCase())
      })
    },
    menus() {
      return this.$store.getters['menus/list']
    }
  },
  async fetch({ store }) {
    store.commit('menus/emptyList')
    const response = await strapi.request('post', '/graphql', {
      data: {
        query: `query {
                    menus {
                        _id
                        name
                        description
                        image {
                            url
                        }
                    }
                }
                `
      }
    })
    response.data.menus.forEach((menu) => {
      menu.image.url = `${apiUrl}${menu.image.url}`
      store.commit('menus/add', {
        id: menu._id,
        ...menu
      })
    })
  }
}
</script>

<style scoped>

</style>
