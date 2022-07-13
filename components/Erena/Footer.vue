<template>
  <div
    class="
      dark:bg-chaos-primary/20 mt-72
      bg-chaos-primary/90
      text-white
      md:h-48
      p-8
      flex flex-col
      space-y-8
      items-center
    "
  >
    <hr class="max-w-6xl border border-chaos-foreground w-full" />
    <div
      class="
        max-w-6xl
        flex flex-col items-center
        md:flex-row md:justify-center
        text-center
        md:text-left
        justify-between
        space-y-4
        md:space-y-0
        items-start
        w-full
      "
    >
      <div class="p-2 flex flex-col space-y-4 items-center text-center">
        <a href="/" class="text-2xl font-black">Go Home</a>
        <span
          class="flex flex-row items-center stroke-chaos-foreground stroke-1 space-x-2"
        >
          <a
            href="https://github.com/retraigo"
            target="_blank"
            class="font-semibold flex flex-row items-center"
          >
            <SVGGitHub />
          </a>
          <a
            href="https://twitter.com/retraigo"
            target="_blank"
            class="font-semibold flex flex-row items-center"
          >
            <SVGTwitter />
          </a>
        </span>
      </div>
    </div>
  </div>
</template>