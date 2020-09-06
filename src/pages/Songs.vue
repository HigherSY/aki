<template>
  <v-row dense>
    <v-col
      v-for="song in songs"
      :key="song.n"
    >
      <SongCard
        :id="song.n"
        :jumpUrl="song.jumpUrl"
        :nick="song.nick"
        :like="song.like"
      />
    </v-col>
  </v-row>
</template>

<script>
import axios from '@/http'
import SongCard from '@/components/SongCard.vue'
export default {
  name: 'index',
  components: {
    SongCard
  },
  data() {
    return {
      songs: null,
    };
  },
  created() {
    axios.get('/songs').then((response) => {
      this.songs = response.data;
      this.songs.sort((a, b) => b.like - a.like);
      this.loading = false;
    });
  },
};
</script>
