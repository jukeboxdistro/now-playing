<template>
  <div class="viewer p-3 overflow-hidden">
    <div v-if="track">
      <div class="media">
        <img :src="track.album.image_url" class="mr-3 rounded" height="75" alt="cover">
        <div class="media-body align-self-center">
          <div class="font-weight-bold text-truncate">{{ track.name }}</div>
          <small class="mb-0 text-white-50 text-truncate">{{ track.album.name }}</small>
        </div>
      </div>
    </div>
    <div v-else>
      <div class="media w-100">
        <img src="https://cdn.jukebox.gg/default.jpg" class="mr-3 rounded" height="75" alt="cover">
        <div class="media-body align-self-center">
          <div class="font-weight-bold text-truncate">Empty Player Queue</div>
          <small class="mb-0 text-white-50 text-truncate">Powered by Jukebox</small>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Twitch from '../mixins/Twitch';

export default {
  name: 'Viewer',

  mixins: [
    Twitch
  ],

  data() {
    return {
      track: null,
    }
  },

  methods: {
    boot () {
      logger('Enabling...');

      this.updateTrack(this.auth.getChannelId());

      this.finishedLoading = true;
    },

    updateTrack(channelId) {
      axios
          .get(`https://api-cache.jukebox.gg/v1/twitch-extensions/${channelId}/currently-playing`)
          .then(response => {
            if (response.status === 204) {
              this.track = null;
            } else {
              this.track = response.data;
            }
            setTimeout(() => this.updateTrack(channelId), 60000);
          })
          .catch(error => {
            console.error(error);
            setTimeout(() => this.updateTrack(channelId), 60000);
          });
    }
  }
}
</script>
