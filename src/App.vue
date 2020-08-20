<template>
  <v-app
    style="
    background: linear-gradient(90deg, #00C9FF 0%, #92FE9D 100%);
    text-align: center;
  "
  >
    <v-navigation-drawer expand-on-hover app right dark>
      <!-- style="background: linear-gradient(270deg, rgba(53,86,255,1) 0%, rgba(129,203,255,1) 100%);" -->
      <v-list>
        <v-list-item class="px-2">
          <v-list-item-avatar color="blue">
            <v-icon dark v-if="!loggedIn">mdi-account-circle</v-icon>
            <v-img
              src="https://cdn.vuetifyjs.com/images/john.jpg"
              v-if="loggedIn"
            ></v-img>
          </v-list-item-avatar>
          <v-list-item-content>
            <v-list-item-title class="title">{{
              !loggedIn ? 'User' : 'Sandra Adams'
            }}</v-list-item-title>
            <!-- <v-list-item-subtitle>{{
              !loggedIn ? 'log in' : ''
            }}</v-list-item-subtitle> -->
          </v-list-item-content>
        </v-list-item>
      </v-list>
      <v-divider></v-divider>
      <v-list nav dense>
        <v-list-item link>
          <v-list-item-icon>
            <v-icon>mdi-folder</v-icon>
          </v-list-item-icon>
          <v-list-item-title>My Files</v-list-item-title>
        </v-list-item>
        <v-list-item link>
          <v-list-item-icon>
            <v-icon>mdi-account-multiple</v-icon>
          </v-list-item-icon>
          <v-list-item-title>Shared with me</v-list-item-title>
        </v-list-item>
        <v-list-item link>
          <v-list-item-icon>
            <v-icon>mdi-star</v-icon>
          </v-list-item-icon>
          <v-list-item-title>Starred</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-spacer></v-spacer>

    <v-main>
      <v-card
        class="mx-auto"
        max-width="60%"
        elevation="24"
        shaped
        style="border: 5px solid lightblue; background: radial-gradient(circle, rgba(119,63,63,1) 0%, rgba(0,0,0,1) 100%); padding: 0px 0px 10px 0px"
      >
        <v-tabs
          color="#58EE9C"
          fixed-tabs
          background-color="transparent"
          dark
          style="padding-bottom: 10px"
        >
          <v-tab>
            Film
          </v-tab>
          <v-tab>
            Actors
          </v-tab>
          <v-tab>
            Director(s)
          </v-tab>
          <v-tab>
            Writer(s)
          </v-tab>
        </v-tabs>
        <!-- take away style and height to fit-->
        <v-img
          contain
          height="400px"
          src="https://m.media-amazon.com/images/M/MV5BMTUyNDIyMTA4NV5BMl5BanBnXkFtZTgwODM2MDMxNjE@._V1_SX300.jpg"
        >
          <template v-slot:placeholder>
            <v-row class="fill-height ma-0" align="center" justify="center">
              <v-progress-circular
                indeterminate
                color="grey lighten-5"
              ></v-progress-circular>
            </v-row> </template
        ></v-img>
        <v-card-title class="justify-center">
          The Stanford Prison Experiment (2015)
          <!-- <v-tooltip right>
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                style="margin-left: 10px"
                icon
                color="#4AD589"
                v-bind="attrs"
                v-on="on"
                href="https://www.imdb.com/title/tt0420293/"
                target="blank"
              >
                <v-icon>mdi-more</v-icon>
              </v-btn>
            </template>
            <span>Click to visit the film's IMDb page</span>
          </v-tooltip>-->
        </v-card-title>
        <v-card-subtitle class="pb-0">Plot</v-card-subtitle>
        <v-card-text class="text--primary">
          <div>
            In 1971, twenty-four male students are selected to take on randomly
            assigned roles of prisoners and guards in a mock prison situated in
            the basement of the Stanford psychology building.
          </div>
        </v-card-text>
        <v-card-actions
          style="justify-content: center; flex-direction: column;"
        >
          <v-slider
            thumb-label="always"
            v-model="rating"
            max="10"
            min="0"
            step=".1"
            color="#4AD589"
            append-icon="mdi-star"
            prepend-icon="mdi-star-off"
            @click:append="rating = rating + 0.1"
            @click:prepend="rating = rating - 0.1"
            style="width: 75%; margin-top: 20px"
          ></v-slider>
          <v-btn
            x-large
            rounded
            color="#58EE9C"
            dark
            style="padding: 0px 20px 0px 20px;"
            v-on:click="showGuessRating = !showGuessRating"
            >Guess IMDb Rating</v-btn
          >
        </v-card-actions>
        <v-card-actions style="justify-content: center">
          <v-tooltip bottom>
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                v-bind="attrs"
                v-on="on"
                text
                color="#4AD589"
                @click="showGuessRating = true"
              >
                Skip
                <v-icon style="padding-left: 10px">mdi-skip-next-circle</v-icon>
              </v-btn>
            </template>
            <span>Skip to the next random movie</span>
          </v-tooltip>
        </v-card-actions>
      </v-card>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  name: 'App',

  components: {
    //
  },

  data: () => ({
    loggedIn: false,
    rating: 5
  })
});
</script>

<style>
html {
  overflow: hidden !important;
  scrollbar-width: none;
  -ms-overflow-style: none;
}

html::-webkit-scrollbar {
  width: 0;
  height: 0;
}
</style>
