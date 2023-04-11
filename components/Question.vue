<template>
  <div class="fullScreen">
    <div class="fullScreenBG"></div>

    <section class="question" v-if="isNotGameOver">
      <span class="counter">{{ qCounter }}.</span>
      <h3 class="questionText">
        {{ question.replace(/^\w/, (c) => c.toUpperCase()) }}
      </h3>
      <h4 class="helpText"></h4>
      Answer:
      <div class="inputWrapper">
        <input
          autocomplete="off"
          spellcheck="false"
          type="text"
          placeholder="Enter your Answer!"
          v-model="inpModel"
          @keyup.enter="submitAnswer"
          style="text-transform: capitalize"
        />
        <span class="inpFocus"></span>
      </div>
    </section>
    <section v-else class="resultDiv">
      <img
        src="https://images.typeform.com/images/KjQ35gfxbQ3e/image/default"
        alt="Throphy"
      />
      <h1 class="resultText">
        <span>Okay, that was pretty hard!</span><br /><span
          >You got {{ goodAnswered }} / {{ maxQuestions }} correct</span
        ><br /><span>You got {{ score }} score!</span><br /><span
          >Finished in {{ time }} seconds</span
        >
      </h1>
    </section>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import wordsDatabaseJSON from '~/static/wordsDatabase.json'
const wordsDatabase: any = wordsDatabaseJSON
export default Vue.extend({
  data() {
    return {
      inpModel: '',
      qCounter: 0,
      randomN: 2,
      question: '',
      answer: '',
      score: 0,
      time: 0,
      goodAnswered: 0,
      maxQuestions: 30,
      isNotGameOver: true,
      currentSection: 'd',
    }
  },
  methods: {
    submitAnswer() {
      if (this.inpModel) {
        if (this.qCounter === this.maxQuestions) {
          this.inpModel = ''
          if (this.inpModel.toLowerCase() === this.answer.toLowerCase())
            return this.endGame(true)
          return this.endGame(false)
        }
        if (this.inpModel.toLowerCase() === this.answer.toLowerCase()) {
          this.loadNewQuestion(true)
        } else {
          console.log(this.inpModel, this.answer)
          this.loadNewQuestion(false)
        }
        this.inpModel = ''
      } else {
        //Handle Plain Input
      }
    },
    initCurrentSection() {
      let pathArr = window.location.pathname.replace('/', '').split('/')
      let currentS = pathArr[0]
      let currentL = pathArr[1]
      const midString = wordsDatabase[currentS][currentL]
      return midString
    },
    endGame(isRight: boolean) {
      isRight ? this.score++ : this.score > 0 ? this.score-- : 0
      isRight ? this.goodAnswered++ : 0
      this.isNotGameOver = false
    },
    loadNewQuestion(saidRight: boolean) {
      saidRight ? this.score++ : this.score > 0 ? this.score-- : 0
      saidRight ? this.goodAnswered++ : 0
      let lastNum = this.randomN
      this.randomN = Math.floor(
        Math.random() * Object.keys(this.currentSection).length
      )
      if (lastNum === this.randomN)
        this.randomN = Math.floor(
          Math.random() * Object.keys(this.currentSection).length
        )
      this.qCounter++
      this.changeQuestions()
    },
    changeQuestions() {
      this.question = Object.keys(this.currentSection)[this.randomN]
      this.answer = Object.values(this.currentSection)[this.randomN]
      if (Math.random() > 0) {
        let temp = this.question
        this.question = this.answer
        this.answer = temp
      }
    },
    startTimer() {
      let refreshIntervalId = setInterval(() => {
        this.isNotGameOver ? this.time++ : clearInterval(refreshIntervalId)
      }, 1000)
    },
  },
  mounted() {
    this.currentSection = this.initCurrentSection()
    this.loadNewQuestion(false)
    this.startTimer()
  },
})
</script>

<style lang="scss" scoped>
.fullScreenBG {
  position: absolute;
  overflow: hidden;
  height: 100vh;
  width: 100vw;
  background: url('~static/engbg.jpg');
  opacity: 0.7;
}
.question {
  max-width: 900px;
  width: 97%;
  min-height: 250px;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  padding: 40px;
  .counter {
    opacity: 0.8;
  }

  .questionText {
    margin-top: 0.2em;
  }
  .helpText {
    color: rgba(0, 0, 0, 0.548);
    font-size: 1.1em;
  }
  h3 {
    margin-bottom: 0.4em;
    font-size: 2em;
    font-weight: 500;
  }
  .inputWrapper {
    max-width: 260px;
    color: #212529;
    font-family: Poppins-Regular, sans-serif;
    border-bottom: 2px solid #d9d9d9;
    margin-top: 5px;
    padding-bottom: 8px;
    transition: all 0.5s;
    &:focus-within {
      border-bottom: 2px solid #02142b;
      color: #02142b;
    }
    input {
      font-size: 1.8em;
      font-weight: 500;
      box-sizing: border-box;
      touch-action: manipulation;
      margin: 0;
      overflow: visible;
      outline: none;
      border: none;
      display: block;
      width: 100%;
      background: 0 0;
      color: #333;
      padding: 0 5px;
      height: 40px;
    }
  }
}
.resultDiv {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
  .resultText {
    color: black;
    margin: 1em;
  }
}
</style>
