<template>
  <div>
    <button class="button" @click="$emit('changeToOptionsView')">BACK</button>
    <p>{{selectedChords}}</p>
  </div>
</template>

<script>
export default {
  data: () => ({
    color: "black",
    isSelected: false
  }),
  props: {
    selectedChords: Array
  },
  methods: {
    greyOutSelected() {
      this.isSelected = !this.isSelected;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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