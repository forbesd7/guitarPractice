<template>
  <div>
    <div v-if="currentView === 'optionsView'" class="container">
      <div class="chordContainer">
        <Chords
          v-for="(chord, index) in chords"
          v-bind:chord="chord"
          v-bind:key="index"
          v-on:addChordToSelected="addChordToSelected"
        ></Chords>
      </div>

      <div class="buttonContainer">
        <button @click="changeToPracticeView" class="button">START</button>
      </div>
    </div>

    <div v-if="currentView === 'practiceView'">
      <ChordSwitchPractice
        v-on:changeToOptionsView="changeToOptionsView"
        v-bind:selectedChords="selectedChords"
        v-bind:beatsPerMin="beatsPerMin"
        v-bind:barsPerChord="barsPerChord"
        v-bind:practiceLength="practiceLength"
      />
    </div>
  </div>
</template>

<script>
import Chords from "./Chords";
import ChordSwitchPractice from "../ChordSwitchPractice";
export default {
  name: "PracticeOptions",
  components: {
    Chords,
    ChordSwitchPractice
  },
  data: () => ({
    currentView: "optionsView",
    practiceLength: 4,
    beatsPerMin: 60,
    barsPerChord: 4,
    selectedChords: [],
    chords: [
      {
        name: "A(maj)",
        sound: ""
      },
      {
        name: "D(maj)",
        sound: ""
      },
      {
        name: "E(maj)",
        sound: ""
      },
      {
        name: "A(min)",
        sound: ""
      },
      {
        name: "E(min)",
        sound: ""
      },
      {
        name: "D(min)",
        sound: ""
      }
    ]
  }),
  methods: {
    addChordToSelected(selectedChord) {
      let checkIfChordHasBeenAdded = false;

      //check if chord has been added, if so, remove from the list
      this.selectedChords.map((chord, index) => {
        if (selectedChord.name === chord.name) {
          this.selectedChords.splice(index, 1);
          checkIfChordHasBeenAdded = true;
          return;
        }
      });

      if (checkIfChordHasBeenAdded === false) {
        this.selectedChords.push(selectedChord);
      }
    },

    changeToPracticeView() {
      this.currentView = "practiceView";
    },
    changeToOptionsView() {
      this.currentView = "optionsView";
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.chordContainer {
  width: 100vw;
  display: flex;
  align-items: center;
  justify-content: center;
}

.buttonContainer {
  padding: 4%;
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
</style>
