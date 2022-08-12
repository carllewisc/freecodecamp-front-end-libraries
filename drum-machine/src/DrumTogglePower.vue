<template>
  <div class="control">
    <p>Power</p>
    <div class="select">
      <div
        class="inner"
        :style="active ? floats.floatR : floats.floatL"
        @click="$emit('update', !active)"
      ></div>
    </div>
  </div>
</template>

<script>
let floats = {
  floatR: {
    float: "right",
  },
  floatL: {
    float: "left",
  },
};

export default {
  emits: ["update"],
  props: {
    active: {
      type: Boolean,
      required: true,
    },
  },
  computed: {
    floats() {
      return floats;
    },
  },
};
</script>
