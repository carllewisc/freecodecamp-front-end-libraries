<template>
  <div
    :id="item.id"
    class="drum-pad"
    :style="drumPad"
    @click="$emit('play-sound', item)"
  >
    <audio class="clip" :id="item.keyTrigger" :src="item.url" />
    {{ item.keyTrigger }}
  </div>
</template>

<script>
let drumPad = {
  backgroundColor: "grey",
  marginTop: "10px",
  boxShadow: "black 3px 3px 5px",
};

export default {
  emits: ["play-sound"],
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  computed: {
    drumPad() {
      return drumPad;
    },
  },
};
</script>
