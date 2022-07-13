<template>
  <ContentDoc v-slot="{ doc }">
    <div
      class="
        flex flex-col text-justify
        md:flex-row
        items-start
        md:justify-start
        space-y-8
        md:space-y-0 md:space-x-8
      "
    >
      <article
        class="
          prose prose-gray order-2
          dark:prose-invert
          prose-code:before:content-none prose-code:after:content-none
        "
      >
        <ContentRenderer :value="doc" />
      </article>
      <BlogTableOfContents :content="doc.body.toc.links" class = "order-1" />
    </div>
  </ContentDoc>
</template>

<style lang="postcss">
/* Customize headers to remove default underline */
.prose h2 a {
  @apply no-underline transition duration-500 ease-in-out block font-bold border-b border-neutral-600 dark:border-neutral-300;
  &:hover {
    @apply text-zinc-600 dark:text-chaos-foreground;
  }
}
.prose h3 a {
  @apply font-semibold no-underline;
}

</style>
<script>
definePageMeta({
  layout: "blog",
  title: "Pranev",
});
</script>