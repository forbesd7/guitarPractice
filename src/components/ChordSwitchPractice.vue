<template>
  <div class="mainContainer">
    <div class="buttonContainer">
      <button class="button" @click="$emit('changeToOptionsView')">BACK</button>
    </div>
    <div style="color:gold">{{localPracticeLength}}</div>
    <div class="chordContainer">
      <div class="countDownTimer" v-if="countdownTimer !== 0">{{countdownTimer}}</div>
      <div style="color:gold" v-else>
        <div v-if="localPracticeLength === 0">Practice Done</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    countdownTimer: 3,
    currentChord: {},
    localPracticeLength: 0,
    practiceStarted: false
  }),
  props: {
    selectedChords: Array,
    practiceLength: Number,
    beatsPerMin: Number,
    barsPerChord: Number
  },
  methods: {
    countDown() {
      const myInterval = setInterval(() => {
        if (this.countdownTimer === 1) {
          clearInterval(myInterval);
        }
        this.countdownTimer--;
      }, 1000);
    },

    startPractice() {
      this.localPracticeLength = this.practiceLength + 2;
      const practiceInterval = setInterval(() => {
        if (this.localPracticeLength === 1) {
          clearInterval(practiceInterval);
          //  this.showFinishedPracticeScreen();
        }
        this.localPracticeLength--;
      }, 1000);
    }

    // showFinishedPracticeScreen() {

    // }
  },
  created() {
    this.countDown();
  },

  updated() {
    if (this.practiceStarted === false) {
      this.practiceStarted = true;
      this.startPractice();
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.mainContainer {
  height: 100vh;
  width: 100vw;
}
.buttonContainer {
  height: 10%;
}
.chordContainer {
  display: flex;
  width: 100vw;
  height: 80%;
  align-items: center;
  justify-content: center;
}
.countDownTimer {
  color: gold;
  font-size: 10em;
}
.button {
  color: gold;
  background: black;
  border: 2px gold solid;
  font-size: 2em;
  transition: 0.5s;
  outline: none;
}
.button:hover {
  background: grey;
  cursor: pointer;
}
@media screen and (max-width: 575px) {
  .chordContainer {
    padding: 2%;
  }
}
</style>

//v-on:click="$emit('addChordToSelected', name)"