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
          <v-list-item-avatar>
            <v-img src="https://randomuser.me/api/portraits/women/85.jpg"></v-img>
          </v-list-item-avatar>
        </v-list-item>

        <v-list-item link>
          <v-list-item-content>
            <v-list-item-title class="title">Sandra Adams</v-list-item-title>
            <v-list-item-subtitle>sandra_a88@gmail.com</v-list-item-subtitle>
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
        max-width="50%"
        elevation="24"
        shaped
        style="border: 5px solid lightblue; background: radial-gradient(circle, rgba(119,63,63,1) 0%, rgba(0,0,0,1) 100%);"
      >
        <v-tooltip top open-delay="500" close-delay="500">
          <template v-slot:activator="{ on, attrs }">
            <v-img
              style="margin-top: 10px;"
              contain
              v-bind="attrs"
              v-on="on"
              height="500px"
              width="100%"
              src="https://m.media-amazon.com/images/M/MV5BMTUyNDIyMTA4NV5BMl5BanBnXkFtZTgwODM2MDMxNjE@._V1_SX300.jpg"
            />
          </template>
          <span>The Standford Prison Experiment (2015)</span>
        </v-tooltip>
        <v-card-title class="justify-center" style="font-size: 32px;">
          The Stanford Prison Experiment
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
        <v-card-subtitle class="pb-0" style="padding: 10px">Plot</v-card-subtitle>
        <v-card-text class="text--primary">
          <div>In 1971, twenty-four male students are selected to take on randomly assigned roles of prisoners and guards in a mock prison situated in the basement of the Stanford psychology building.</div>
        </v-card-text>
        <v-card-actions style="justify-content: center; flex-direction: column;">
          <v-btn
            x-large
            rounded
            v-if="showGuessRating"
            color="#58EE9C"
            dark
            style="padding: 30px"
            v-on:click="showGuessRating=!showGuessRating"
          >Guess Rating</v-btn>
          <v-slider
            v-if="!showGuessRating"
            v-model="slider"
            thumb-label="always"
            max="10"
            min="0"
            step=".1"
            color="#4AD589"
            style="padding: 30px 30px 0px 30px; width: 100%"
          ></v-slider>
        </v-card-actions>
        <v-card-actions style="justify-content: center">
          <v-tooltip bottom>
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                v-bind="attrs"
                v-on="on"
                text
                color="#4AD589"
                @click="showGuessRating=true"
                style="margin: 10px"
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
import Vue from "vue";

export default Vue.extend({
  name: "App",

  components: {
    //
  },

  data: () => ({
    showGuessRating: true
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
