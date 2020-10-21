<template>
  <div>
    <p>First name: {{ firstName }}</p>
    <p>Last name: {{ lastName }}</p>
    <p>Full name: {{ fullName }}</p>
  </div>
</template>

<script>
export default {
  name: "Name",
  data: function() {
    return {
      firstName: "Madison",
      lastName: "Hu"
    };
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
    }
  }
};
</script>

<style scoped></style>
