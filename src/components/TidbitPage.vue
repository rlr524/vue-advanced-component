<template>
  <article-layout>
    <template #articleHeader>
      <h1>I am the header</h1>
    </template>
    <template #articleContent>
      <p>I am the content</p>
    </template>
    <template #articleFooter>
      <footer>I am the footer</footer>
    </template>
    <template #side>
      <aside>I am the side stuff</aside>
    </template>
    <template #banner>
      <div>I am the banner</div>
    </template>
  </article-layout>
</template>

<script>
import ArticleLayout from "@/components/ArticleLayout.vue";

export default {
  name: "TidbitPage",
  components: {
    articleLayout: ArticleLayout
  }
};
</script>

<style lang="scss" scoped></style>
