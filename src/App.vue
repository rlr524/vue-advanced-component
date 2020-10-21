<template>
  <div id="app" class="container">
    <div class="col-xs-12">
      <app-quote :quote="'This is being passed using props.'">
        <h1>{{ quoteTitle }}</h1>
        <h2>
          This is using our slot. We style it in the component using the slot,
          not here.
        </h2>
        <p>
          So is this. Slots work well for content; props should still be used
          for data, particularly changes in state.
        </p>
      </app-quote>
      <app-name></app-name>
      <hr />
      <app-question></app-question>
      <hr />
    </div>
  </div>
</template>

<script>
import Quote from "@/components/Quote.vue";
import Name from "@/components/Name.vue";
import Question from "@/components/Question.vue";

export default {
  name: "App",
  components: {
    appQuote: Quote,
    appName: Name,
    appQuestion: Question
  },
  data: function() {
    return {
      quoteTitle:
        "This is the quote title. It is data passed in our root instance. It still gets styled in our child component."
    };
  }
};
</script>

<style scoped>
hr {
  height: 1px;
  background: black;
}
</style>
