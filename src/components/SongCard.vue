<template>
  <v-card width="300">
    <v-card-title>{{ id }}</v-card-title>
    <Meting :auto="jumpUrl" />
    <v-card-text>{{ nick }} {{ like }}</v-card-text>
    <v-card-actions>
      <v-btn text @click="submit_like">送我上去</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
import axios from "@/http";
export default {
  name: "songcard",
  props: {
    id: {
      required: true,
      type: Number,
    },
    nick: {
      required: true,
      type: String,
    },
    like: {
      required: true,
      type: Number,
    },
    jumpUrl: {
      required: true,
      type: String,
    },
  },
  methods: {
    submit_like() {
      axios.post('/song/' + this.id + '/like').then(() => {
        this.like++;
      });
    },
  },
};
</script>
