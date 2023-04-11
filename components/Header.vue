<template>
  <div class="fullScreen">
    <div class="left">
      <h5 class="logo">speedlang</h5>
      <h1 class="mainText">Practice & Learn Language you Love!</h1>

      <button class="btn" @click="scroll">Get Started</button>
    </div>
    <div class="right"></div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  methods: {
    scroll() {
      window.scroll({
        top: 1000,
        behavior: 'smooth',
      })
    },
  },
})
</script>

<style lang="scss" scoped>
.fullScreen {
  height: 100vh;
  width: 100%;
  background-color: #02142b;
  color: white;
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  position: relative;
  .left {
    width: 50%;
    height: 100%;
    padding: 15vh 2vw 0 5vw;

    .mainText {
      margin-top: 1em;
    }
    .lightText {
      color: rgba(255, 255, 255, 0.5);
      margin-top: 0.7em;
    }
    h1 {
      font-size: 6em;
      font-weight: bold;
    }
    h4 {
      font-size: 2em;
    }
    h5 {
      font-size: 2em;
    }
    .btn {
      cursor: pointer;
      width: 7.5em;
      height: 2.5em;
      border-radius: 1em;
      margin-top: 3em;
      font-weight: bold;
      font-size: 2em;
    }
  }
  .right {
    width: 50%;
    height: 100%;
    background: url('~static/langbg.jpg');
    position: relative;
    order: 2;
    overflow: hidden;
    height: 100%;
    order: 1;
  }
}
</style>
