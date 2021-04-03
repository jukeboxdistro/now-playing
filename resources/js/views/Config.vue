<template>
    <div class="vh-100 d-flex justify-content-center">
      <div class="col-8 align-self-center text-center">
        <img src="https://cdn.jukebox.gg/default.jpg" class="mb-3 rounded" height="75" alt="cover">
        <h3>Welcome to Jukebox!</h3>
        <h5 class="text-white-50">
          The Music Player for Streamers & Gamers
        </h5>

        <p class="py-5 text-white-50">
          Jukebox is a music streaming platform, created by Streamers & 3rd Party Twitch Devs for streamers. Together with our artist partners we want to offer a DMCA free solution to streamers that does not mute VODs or clips or remove their music from them.
        </p>

        <a href="https://play.jukebox.gg/" class="btn btn-lg btn-primary mr-4" target="_blank">
          Open Webplayer
        </a>
        <a href="https://jukebox.gg/partnership" class="btn btn-lg btn-outline-light" target="_blank">
          Sign up as Artist
        </a>
      </div>
    </div>
</template>

<script>
import Twitch from '../mixins/Twitch';

export default {
    name: 'Config',

    mixins: [
        Twitch
    ]
}
</script>
