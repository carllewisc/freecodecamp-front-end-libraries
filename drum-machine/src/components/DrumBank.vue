<template>
  <div class="control">
    <p>Bank</p>
    <div class="select">
      <div
        class="inner"
        :style="active ? floats.floatR : floats.floatL"
        @click="power ? $emit('change-bank') : null"
      />
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
  emits: ["change-bank"],
  props: {
    active: {
      type: Boolean,
      required: true,
    },
    power: {
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
