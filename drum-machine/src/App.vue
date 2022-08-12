<template>
  <header>
    <div class="wrapper"></div>
  </header>

  <main>
    <drum-machine />
  </main>
</template>

<style>
@import "./assets/base.css";
</style>
<script>
import DrumMachine from "./components/DrumMachine.vue";
export default {
  components: { DrumMachine },
};
</script>
