<template>
  <div>
    <p>First name: {{ firstName }}</p>
    <p>Last name: {{ lastName }}</p>
    <p>Full name: {{ fullName }}</p>
    <div v-bind:class="{ active: isActive, 'text-danger': hasError }">
      <p>This sentence changes color based on the button or the slider.</p>
      <button class="button" @click="applyActive">Apply Active</button>
      <input
        type="range"
        name="slider"
        id="slider"
        step="10"
        min="0"
        max="100"
        @change="applySlider"
      />
    </div>
    <br />
    <div v-bind:class="classObject">
      <p>This sentence uses a computed property to change color.</p>
      <button class="button" @click="applyError">Throw an error</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Name",
  data: function() {
    return {
      firstName: "Madison",
      lastName: "Hu",
      isActive: false,
      hasError: false,
      value: 0,
      isActiveTwo: true,
      error: false
    };
  },
  methods: {
    applyActive: function() {
      this.isActive ? (this.isActive = false) : (this.isActive = true);
    },
    applySlider: function() {
      this.hasError ? (this.hasError = false) : (this.hasError = true);
    },
    applyError: function() {
      this.isActiveTwo ? (this.isActiveTwo = false) : (this.isActiveTwo = true);
      this.error ? (this.error = false) : (this.error = true);
    }
  },
  computed: {
    fullName: {
      get: function() {
        return this.firstName + " " + this.lastName;
      },
      set: function() {
        var names = newName.split(" ");
        this.firstName = names[0];
        this.lastName = names[1];
        console.log(newName);
      }
    },
    classObject: function() {
      return {
        "active-two": this.isActiveTwo && !this.error,
        "text-danger-two": !this.isActiveTwo && this.error
      };
    }
  }
};
</script>

<style>
.button {
  margin-right: 2%;
}
.active {
  color: purple;
}
.active-two {
  color: aqua;
}
.text-danger {
  color: red;
}
.text-danger-two {
  color: red;
}
</style>
