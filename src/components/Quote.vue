<template>
  <div>
    <h3>This is a great quote</h3>
    <p>{{ quote }}</p>
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "Quote",
  props: {
    quote: {
      type: String,
      required: false
    }
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

h1 {
  color: green;
}

h2 {
  color: red;
}
</style>
