<template>
  <div class="header">
    <div class="header-wrap">
      <a href="/" class="header-wrap__link">
        <div class="header-wrap__link-img"></div>
      </a>
    </div>
  </div>
</template>

<script lang="ts"></script>

<style lang="scss" scoped>
.header {
  width: 100%;
  padding: 15px 0;
  background: #02142b;
  .header-wrap {
    max-width: 1080px;
    width: 97%;
    margin: 0 auto;
    .header-wrap__link {
      text-decoration: none;
      display: inline-block;
    }
    .header-wrap__link-img {
      width: 10em;
      height: 2em;
      background: url('~/static/logo.png') no-repeat 50% / cover;
    }
  }
}
</style>
