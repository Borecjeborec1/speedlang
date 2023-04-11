<template>
  <div class="fullScreen">
    <div class="hrefs">
      <div class="wrapper">
        <router-link
          v-for="(lection, ind) in lections"
          :key="ind"
          class="singleWrep"
          :to="lection.path"
        >
          <h3>{{ lection.name }}</h3>
          <p>
            {{ lection.text }} <br />
            {{ lection.example }}
          </p>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
import sections from '~/static/sections.json'

export default {
  data() {
    return {
      lections: undefined,
    }
  },
  methods: {
    addPaths() {
      this.lections.forEach((el) => {
        el.path =
          window.location.pathname +
          '/' +
          el.name.replace(/ +/g, '').replace('/', '').toLowerCase()
      })
    },
    initPath() {
      let path = window.location.pathname.replace('/', '')
      this.lections = sections[path]
    },
  },
  mounted() {
    this.initPath()
    this.addPaths()
  },
}
</script>

<style lang="scss" scoped>
body {
  overflow-x: hidden;
}
.fullScreen {
  margin: 3em auto 3em;
  .hrefs {
    padding: 0 8rem;
    margin: 0 auto;
    width: 95%;
    .wrapper {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      .singleWrep {
        cursor: pointer;
        font-size: 110%;
        width: 25%;
        margin: 0 3em 2em;
        .number {
          position: relative;
          margin-bottom: 2rem;
          width: 3rem;
          height: 3rem;
          text-align: center;
        }

        h3 {
          display: inline-block;
          margin-bottom: 0.2rem;
          font-size: 2.5rem;
          font-weight: 500;
          color: inherit;
        }
        p {
          margin-top: 1rem;
          line-height: 150%;
          color: #7c8897;
        }
      }
    }
  }
}
</style>
