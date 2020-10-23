<template>
  <div>
    <h3>New quote</h3>
    <button @click="increaseCounter">Increase!</button>
    <p>The counter is at {{ counter }}</p>
  </div>
</template>

<script>
export default {
  name: "New",
  data: function() {
    return {
      counter: 0
    };
  },
  methods: {
    increaseCounter: function() {
      this.counter += 1;
    }
  },
  destroyed() {
    console.log("Destroyed");
  },
  deactivated() {
    console.log("Deactivated");
  },
  activated() {
    console.log("Activated");
  }
};
</script>

<style scoped>
div {
  border: 1px solid black;
  box-shadow: 1px 1px 2px black;
  padding: 30px;
  margin: 30px auto;
  text-align: center;
}
</style>
