<template>
  <div>
    <article>
      <slot name="articleHeader" />
      <slot name="articleContent" />
      <slot name="articleFooter" />
    </article>
    <aside>
      <slot name="side" />
    </aside>
    <div>
      <slot name="banner" />
    </div>
  </div>
</template>

<script>
export default {
  name: "ArticleLayout"
};
</script>

<style scoped>
article {
  color: purple;
}
</style>
