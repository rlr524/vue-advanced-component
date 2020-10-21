<template>
  <div id="question">
    <p>
      Ask a yes / no question
      <input v-model="question" type="text" />
    </p>
    <p>{{ answer }}</p>
  </div>
</template>

<script>
import axios from "axios";
import _debounce from "lodash/debounce";
import _capitalize from "lodash/capitalize";

export default {
  name: "Question",
  data: function() {
    return {
      question: "",
      answer: "I cannot give you an answer until you ask a question!"
    };
  },
  watch: {
    // Whenever the question changes, this function will run
    // This is a good example of using watch as it allows us to perform an async
    // operation (accessing the yesno api), limit how often we perform the operation
    // and set the intermediary states until we get the final answer
    question: function(newQuestion, oldQuestion) {
      this.answer = "Waiting for you to stop typing...";
      this.debouncedGetAnswer();
    }
  },
  created: function() {
    // _debounce is a function provided by lodash to limit how
    // often a particularly expensive operation can be run.
    // In this case, we want to limit how often we access
    // yesno.wtf/api, waiting until the user has completely
    // finished typing before making the ajax request. To learn
    // more about the _debounce function (and its cousin
    // _throttle), visit: https://lodash.com/docs#debounce
    // The syntax is _debounce(function, wait in # ms, options)
    // What debounce basically does is it delays invoking the function
    // until after a wait of # ms since the last time the function was invoked
    this.debouncedGetAnswer = _debounce(this.getAnswer, 500);
  },
  methods: {
    getAnswer: function() {
      if (this.question.indexOf("?") === -1) {
        this.answer = "Questions usually contain a question mark. ;-)";
        return;
      }
      this.answer = "Thinking...";
      var vm = this;
      axios
        .get("https://yesno.wtf/api")
        .then(function(res) {
          vm.answer = _capitalize(res.data.answer);
        })
        .catch(function(error) {
          vm.answer = "Error! Could not reach the Yes/No api. " + error;
        });
    }
  }
};
</script>

<style scoped></style>
