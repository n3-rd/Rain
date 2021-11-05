<template>
  <div>
    <q-dialog
      v-model="soundDialog"
      persistent
      maximized
      transition-show="slide-up"
      transition-hide="slide-down"
    >
      <q-card class="bg-primary text-white">
        <!-- <q-icon
          name="keyboard_arrow_down"
          class="fixed-top-right q-pr-md q-pt-md"
          v-close-popup
          size="xl"
        /> -->
        <SoundPopup :soundName="currentSound" />
      </q-card>
    </q-dialog>

<transition-group
  appear
  enter-active-class="animated fadeIn"
  leave-active-class="animated fadeOut"
>
    <div class="container">
      <div class="row q-pr-md q-py-xl">
        <!-- <q-icon
          name="music_note"
          class="music-playing absolute-top-right bg-primary q-pa-sm animated rotateIn fadeOut infinite"
          size="xl"
        /> -->
         <q-spinner-bars
          class="music-playing absolute-top-right bg-primary q-pa-sm q-mr-sm animated rotateIn fadeOut infinite"
          size="xl"
          v-show="soundPlaying"
          @click="soundDialog = true"
        />

        <div
          class="col-xs-6 col-lg-3 col-md-3 q-gutter-md sound-container"
          v-for="sound in sounds"
          :key="sound.index"
        >
          <q-card
            class="sound-container-card"
            v-ripple
            @click="playSound(sound.link, sound.name, sound.index)"
          >
            <q-card-section class="sound-name text-h6 text-weight-bold q-pb-xl">
              {{ sound.name }}
            </q-card-section>
            <q-card-section class="sound-number text-h4 text-weight-bolder">
              {{ sound.index }}
              <q-icon name="play_circle_fill" class="float-right" />
            </q-card-section>
          </q-card>
        </div>
      </div>
    </div>
</transition-group>
  </div>
</template>

<style lang="scss">
.sound-container {
  cursor: pointer;
  margin: 33px auto;
  .sound-container-card {
    background: #554a96;
    background-image: url(~assets/pattern-1.svg);
    border-radius: 15px;
  }
  .sound-number {
    opacity: 0.7;
  }
  .sound-name {
    opacity: 0.5;
  }
}
.music-playing {
  border-radius: 50%;
}
</style>
<script>
import { Howl, Howler } from "howler";
import SoundPopup from "components/SoundPopup";
export default {
  name: "Sounds",
  components: {
    SoundPopup,
  },
  data() {
    return {
      sounds: [
        {
          name: "Light",
          index: "01",
          link: "http://localhost:1987/light_1.mp3",
        },
        {
          name: "Light",
          index: "02",
          link: "http://localhost:1987/light_2.mp3",
        },
        {
          name: "Light",
          index: "03",
          link: "http://localhost:1987/light_3.mp3",
        },
        {
          name: "Heavy",
          index: "01",
          link: "http://localhost:1987/heavy_1.mp3",
        },
        {
          name: "Heavy",
          index: "02",
          link: "http://localhost:1987/heavy_2.mp3",
        },
      ],
      soundDialog: false,
      currentSound: "",
      soundPlaying: false,
          noPlayedSounds : '',
    };
  },
  methods: {
    playSound: function (sound, soundName, soundIndex) {
      Howler.stop();
      localStorage.setItem('lastPlayedSound', soundName+' '+soundIndex)

      this.soundDialog = true;

    
      
      var sound = new Howl({
        src: [sound],
        html5: true,
        loop: true,

      });

      
      this.noPlayedSounds++;
      console.log(this.noPlayedSounds)
      localStorage.setItem('noPlayedSounds', this.noPlayedSounds)
      sound.play();
      this.currentSound = soundName+' '+soundIndex;
    },
  },
  created(){
    if(!localStorage.getItem('noPlayedSounds')){
      localStorage.setItem('noPlayedSounds', 0)
    }
    this.noPlayedSounds = localStorage.getItem('noPlayedSounds')
    
  },
  updated(){
// if(sound.se)

  },
  mounted(){
  // this.isMusicPlaying()

  }
};
</script>
