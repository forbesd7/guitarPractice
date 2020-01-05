<template>
  <div
    class="chordContainer"
    v-bind:class="{selected: isSelected}"
    @click="() => {greyOutSelected(); $emit('addChordToSelected', chord)}"
  >
    <p>{{ chord.name }}</p>
  </div>
</template>

<script>
export default {
  data: () => ({
    color: "black",
    isSelected: false
  }),
  props: {
    chord: Object
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
.chordContainer {
  font-size: 2em;
  padding: 3%;
  color: gold;
  border: 2px gold solid;
  border-radius: 6hpx;
  margin-right: 2%;
  margin-left: 2%;
  transition: 0.3s;
}
.selected {
  background: grey;
}
.chordContainer:hover {
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