<template>
  <div id="app" class="container">
    <div class="col-xs-12">
      <!-- We're using dynamic components here, which destroy and reload the component when we navigate to/away from it by default -->
      <!-- We avoid destroying the component(s) by wrapping the component call in the "keep-alive" element; keep in mind this only avoids
      destroying them when going from one dynamic component to another, not, for example, on a full page reload of  the app  -->
      <button @click="selectedComponent = 'appQuote'">Quotes</button>
      <button @click="selectedComponent = 'appAuthor'">Author</button>
      <button @click="selectedComponent = 'appNew'">New</button>
      <hr />
      <keep-alive>
        <component :is="selectedComponent">
          <h1>{{ quoteTitle }}</h1>
          <h2>
            This is using our slot. We style it in the component using the slot,
            not here.
          </h2>
          <p>
            So is this. Slots work well for content; props should still be used
            for data, particularly changes in state.
          </p>
        </component>
      </keep-alive>
      <!-- <app-quote :quote="'This is being passed using props.'">
      </app-quote> -->
      <app-name></app-name>
      <hr />
      <app-question></app-question>
      <hr />
      <tidbit-page></tidbit-page>
    </div>
  </div>
</template>

<script>
import Quote from "@/components/Quote.vue";
import New from "@/components/New.vue";
import Author from "@/components/Author.vue";
import Name from "@/components/Name.vue";
import Question from "@/components/Question.vue";
import TidbitPage from "@/components/TidbitPage.vue";

export default {
  name: "App",
  data: function() {
    return {
      quoteTitle:
        "This is the quote title. It is data passed in our root instance. It still gets styled in our child component.",
      selectedComponent: "appQuote"
    };
  },
  components: {
    appQuote: Quote,
    appAuthor: Author,
    appNew: New,
    appName: Name,
    appQuestion: Question,
    tidbitPage: TidbitPage
  }
};
</script>

<style scoped>
#app {
  margin-top: 2%;
}
hr {
  height: 1px;
  background: black;
}
</style>
