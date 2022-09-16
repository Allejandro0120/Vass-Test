<template>
  <v-container fluid class="pa-0">
    <v-row>
      <v-col 
        cols="12" 
        class="pt-0"
      >
        <v-card
          width="100vw"
          height="80vh"
          class="top--card"
          color="rgba(252,117,140)"
        >
          <v-card-title class="top--card--title">
            EXPLORE BEYOND YOUR HORIZON
          </v-card-title>
          <v-card-title class="top--card--subtitle pb-0">
            Magna mundi refereentur quo, no rebum dignissim qui.
          </v-card-title>
          <v-card-title class="top--card--subtitle pt-0">
            Per quodsi accusata id, agam labores.
          </v-card-title>
          <v-card-actions>
            <v-btn type="submit" tile class="pa-5" x-small height="10px" color="rgba(252,117,140)">VIEW OUR WORK</v-btn>
          </v-card-actions>
        </v-card>
      </v-col>

    </v-row>
    <v-row>
      <v-col class="d-flex justify-center">
        <v-btn
            text
            color="rgba(252,117,140)"
            @click="getDataApi()"
          > Todos
        </v-btn>
        <v-btn
            text
            color="rgba(252,117,140)"
            @click="getDataApi('Par')"
          > Par
        </v-btn>
        <v-btn
            text
            color="rgba(252,117,140)"
            @click="getDataApi('Impar')"
          > ImPar
        </v-btn>
      </v-col>
    </v-row>
    <v-row>
      <v-col class="d-flex align-center justify-center">
        <v-flex md8>
          <v-col cols="12">
            <v-container class="grey lighten-5">
              <v-row
                no-gutters
                style="height: 150px;"
              >
                <v-col cols="4"
                  v-for="photo in photos"
                  :key="photo.id"
                  align-self="end"
                >
                  <v-card
                    class="pa-2 ma-3"
                    outlined
                    tile
                  >
                    <v-img :src="photo.url" height="" :alt="photo.title"></v-img>
                  </v-card>
                </v-col>
              </v-row>
            </v-container>
          </v-col>
        </v-flex>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  import axios from 'axios'
  export default {
    name: 'Home',

    data () {
      return {
        photos: [],
        loadError: false
      }
    },
    methods: {
      async getDataApi (selector) {
        try {
          const result = await axios.get('https://jsonplaceholder.typicode.com/albums/1/photos')
          this.photos = result.data
          if (selector === 'Par') {
            this.photos = this.photos.filter(item => item.id % 2 === 0)
          } else if (selector === 'Impar') {
            this.photos = this.photos.filter(item => item.id % 2 !== 0)
          }
        } catch (error) {
          console.log(error)
          this.loadError = true
        }
      }
    },
    mounted () {
      this.getDataApi()
    }
  }
</script>

<style>
  .top--card {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    font-size: 18px;
    margin-top: 0;
    padding-top: 0;
    color: white;
  }
  .top--card--title {
    color: white;
    font-size: 2em;
  }
  .top--card--subtitle {
    color: white;
    font-size: 1em;
    max-width: 30%;
  }
</style>
