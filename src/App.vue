<template>
  <div id="app">
    <div class="home" v-if="step===0">
      <input type="radio" name="sex" ref="man" @click="man">男
      <input type="radio" name="sex" ref="women" @click="women">女
    </div>
    <div class="video">
      <vue-fullscreen-video style="position: absolute" v-show="step===1" @stop="onStop" ref="player"
                            :auto-play="false" :loop="false"
                            align="crop"
                            :url="video" :style="{background: '#000'}">

      </vue-fullscreen-video>
      <vue-fullscreen-video style="position: absolute" v-show="step===2" @stop="onStop" ref="players"
                            :auto-play="false" :loop="false"
                            align="crop"
                            :url="videos" :style="{background: '#000'}">

      </vue-fullscreen-video>
    </div>
  </div>
</template>

<script>
  import fastclick from 'fastclick'
  import VueFullscreenVideo from "vue-fullscreen-video"
  import video from "./assets/video/mimo.mp4"
  import videos from "./assets/video/row.mp4"
export default {
    components:{VueFullscreenVideo},
  name: 'app',
  data () {
    return {
        step:0,video:video,videos:videos,
    }
  },
  methods:{
     man(){
       this.step=1;
       this.$refs.player.play();
       this.$refs.player.update();
     },
    onStop(){
       this.step=0;
    },
    women(){
        this.step=2;
        this.$refs.players.play();
        this.$refs.players.update();
    }
  },
  mounted: function () {
    fastclick.attach(this.$el)
  }
}
</script>

<style>
@import "assets/css/base.css";
@import "assets/css/mobile_h5.css";
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
