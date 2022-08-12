<template>
  <div class="volume-slider">
    <input
      type="range"
      step="0.01"
      min="0"
      max="1"
      :value="volume"
      @change="$emit('update', $event.target.value)"
    />
  </div>
</template>

<script>
export default {
  emits: ["update"],
  props: {
    volume: {
      type: [Number, String],
      required: true,
      default: 0,
    },
  },
};
</script>
