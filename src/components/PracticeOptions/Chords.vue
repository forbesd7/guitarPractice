<template>
  <div
    class="chordContainer"
    v-bind:class="{chordContainer2: isActive}"
    v-on:click="greyOutSelected"
  >
    <p>{{ name }}</p>
    <p>{{fack}}</p>
  </div>
</template>

<script>
export default {
  data: () => ({
    color: "black",
    isActive: false
  }),
  props: {
    name: String
  },
  methods: {
    greyOutSelected() {
      this.isActive = !this.isActive;
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
.chordContainer2 {
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

// v-on:click="$emit('addChordToSelected', name)"