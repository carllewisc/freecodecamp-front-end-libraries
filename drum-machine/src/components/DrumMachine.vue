<template>
  <div id="drum-machine" class="inner-container">
    <div class="pad-bank">
      <template v-if="soundsOne.length">
        <DrumPad
          v-for="item in soundsOne"
          :key="item.id"
          :item="item"
          @play-sound="onPlaySound"
        />
      </template>
    </div>

    <div class="controls-container">
      <DrumTogglePower :active="powerActive" @update="powerActive = $event" />

      <p id="display">{{ idKey ? idKey : null }}</p>
      <DrumVolume :volume="volume" @update="volume = $event" />

      <DrumBank
        :active="bank"
        :power="powerActive"
        @change-bank="onChangeBank"
      />
    </div>
  </div>
</template>

<script>
import data from "./../assets/data.json";
import DrumPad from "./DrumPad.vue";
import DrumTogglePower from "../DrumTogglePower.vue";
import DrumVolume from "./DrumVolume.vue";
import DrumBank from "./DrumBank.vue";

export default {
  components: { DrumBank, DrumVolume, DrumTogglePower, DrumPad },
  data: () => ({
    soundsOne: [],
    soundsTwo: [],
    powerActive: false,
    soundsPlayOne: true,
    volume: 0,
    power: true,
    bank: true,
    idKey: "",
    keyTrigger: "q",
  }),
  mounted() {
    this.soundsOne = data[0];
    this.soundsTwo = data[1];
    document.addEventListener("keydown", this.onHandleKeyPress);
  },
  unmounted() {
    document.addEventListener("keydown", this.onHandleKeyPress);
  },
  methods: {
    onPlaySound({ keyCode, keyTrigger, id, url }) {
      this.idKey = id;
      // this.idKey = id.replace(/-/g, " ");
      this.keyTrigger = keyTrigger;
      // this.setState({ idKey: id, keyTrigger });
      const sound = document.getElementById(keyTrigger);
      sound.currentTime = 0;
      sound.play();
      sound.volume = this.volume;
    },
    onChangeBank() {
      this.bank = !this.bank;
      this.soundsPlayOne = !this.soundsPlayOne;
    },
    onHandleKeyPress(event) {
      this.keyTrigger = event.key;
      let key = this.keyTrigger;

      if (event.key === key) {
        let keyTrigger = key.toUpperCase();
        const id = this.soundsOne.find(
          (item) => item.keyTrigger === keyTrigger
        )?.id;
        console.info(id);
        this.onPlaySound({ keyCode: "", keyTrigger, id, url: "" });
      }
    },
  },
};
</script>
