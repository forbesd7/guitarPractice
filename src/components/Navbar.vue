<template>
  <div class="navbar">
    <div class="navbar__practiceOption">
      <p>Listening</p>
    </div>
    <div class="navbar__practiceOption">
      <p>Chord Switches</p>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({}),
  props: {},
  methods: {}
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.navbar {
  background-color: palegoldenrod;
  color: black;
  display: flex;
  justify-content: center;
  height: 10%;
  width: 100%;
  align-items: center;
}

.navbar__practiceOption {
  transition: 0.3s;
  font-size: 2rem;
  border: 2px black solid;
  flex-grow: 2;
  text-align: center;
}
.navbar__practiceOption:hover {
  background-color: grey;
  cursor: pointer;
}
</style>
