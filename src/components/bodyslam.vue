<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="info">
      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item to="/">Home</b-nav-item>
          <b-nav-item to="/about">About</b-nav-item>
        </b-navbar-nav>

        <!-- Right aligned nav items -->

        <b-navbar-nav class="ml-auto">
          <b-input
            size="sm"
            class="mr-sm-2"
            placeholder="Search"
            type="text"
            v-model="textSearch"
          />
          <b-button
            @click="searchData()"
            size="sm"
            class="my-2 my-sm-0"
            type="submit"
            >Seacrh</b-button
          >
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
    <div class="row">
      <br />
      <b-container fluid class="p-4 bg-dark">
        <b-col> 
          <b-card
            v-for="list in playList"
            :key="list.trackId"
            :title="list.artistName"
            :img-src="list.artworkUrl60"
            :img-alt="list.artistName"
            img-buttom
            tag="article"
            style="max-width: 20rem"
            class="mb-2"
          >
            <b-card-text>
              {{ list.kind }} : {{ list.trackName }}
              <audio controls>
                <source :src="list.previewUrl" type="audio/mpeg" />
                Your browser
              </audio>
            </b-card-text>

            <b-button :href="list.trackViewUrl" variant="primary"
              >Go somewhere</b-button
            >
          </b-card>
        </b-col>
      </b-container>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      playList: [],
      textSearch: "",
    };
  },

  methods: {
    searchData() {
      axios
        .get('https://itunes.apple.com/search?term=bodyslam')
        .then((response) => {
          this.playList = response.data.results;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>

<style>

</style>