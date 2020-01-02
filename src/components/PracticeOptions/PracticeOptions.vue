<template>
  <div class="container">
    <!-- <button>Start</button>
    <button>Time</button>-->

    <Chords
      v-for="(chord, index) in chords"
      v-bind:name="chord.name"
      v-bind:key="index"
      v-on:addChordToSelected="addChordToSelected"
    ></Chords>
    <p style="color:gold">{{ selectedChords }}</p>
  </div>
</template>

<script>
import Chords from "./Chords";
export default {
  name: "PracticeOptions",
  components: {
    Chords
  },
  data: () => ({
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
      this.selectedChords.push(selectedChord);
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
  align-items: center;
  justify-content: center;
}
</style>
