<template>
  <div class="fullScreen">
    <div class="tos">
      <div class="wrapper">
        <router-link class="singleWrep" to="/germany">
          <div class="number number__triangle"></div>
          <h3>Practice Germany →</h3>
          <p>
            By choosing a set of colors, you'll train a neural network powered
            algorithm to generate colors you like and block ones you don’t,
            right in your browser.
          </p>
        </router-link>
        <router-link class="singleWrep" to="/spanish">
          <div class="number number__square"></div>
          <h3>Practice Spanish →</h3>
          <p>
            By choosing a set of colors, you'll train a neural network powered
            algorithm to generate colors you like and block ones you don’t,
            right in your browser.
          </p>
        </router-link>
        <router-link class="singleWrep" to="/germany">
          <div class="number number__circle"></div>
          <h3>A personalized algorithm →</h3>
          <p>
            By choosing a set of colors, you'll train a neural network powered
            algorithm to generate colors you like and block ones you don’t,
            right in your browser.
          </p>
        </router-link>
        <router-link class="singleWrep" to="/germany">
          <div class="number number__diamond"></div>
          <h3>A personalized algorithm →</h3>
          <p>
            By choosing a set of colors, you'll train a neural network powered
            algorithm to generate colors you like and block ones you don’t,
            right in your browser.
          </p>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script lang="ts"></script>

<style lang="scss" scoped>
body {
  overflow-x: hidden;
}
.fullScreen {
  margin: 10em auto 3em;
  .tos {
    padding: 0 8rem;
    margin: 0 auto;
    width: 95%;
    .wrapper {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      margin-top: 7rem;
      .singleWrep {
        cursor: pointer;
        font-size: 140%;
        width: 45%;
        margin-bottom: 6em;
        .number {
          position: relative;
          margin-bottom: 2rem;
          width: 3rem;
          height: 3rem;
          text-align: center;
        }
        .number.number__triangle {
          width: 0;
          height: 0;
          line-height: 6.5rem;
          margin-top: -0.5rem;
          border-left: 2rem solid transparent;
          border-right: 2rem solid transparent;
          border-bottom: 3.5rem solid #faf0a3;
          color: #f58f8d;
        }
        .number.number__square {
          background-color: #f58f8d;
          color: #4e42f9;
        }
        .number.number__circle {
          background-color: #cb355f;
          border-radius: 50%;
          width: 4rem;
          height: 4rem;
          line-height: 4rem;
          color: #faf0a3;
        }
        .number.number__diamond {
          background-color: #4e42f9;
          color: #f58f8d;
          width: 3rem;
          height: 3rem;
          line-height: 3rem;
          transform: rotateZ(45deg);
        }
        h3 {
          display: inline-block;
          margin-bottom: 1rem;
          font-size: 2.8rem;
          font-weight: 500;
          color: inherit;
        }
        p {
          margin-top: 1rem;
          line-height: 150%;
          color: #8999b0;
        }
      }
    }
  }
}
</style>
