<template>
  <div class="flex flex-col items-center space-y-72">
    <div class="flex flex-col items-center mt-36">
      <CardPerson
        name="Pranev (NeTT)"
        title="Open-Source Supremacist"
        description="I make web apps and random libraries in JavaScript / Typescript."
        image="/nett.png"
      />
    </div>
    <div class="flex flex-col items-center">
      <CardPlain
        title="About Me"
        :description="[
          `I'm Pranev, aka NeTT, a college student who makes random JavaScript programs in my free time. I usually make websites and web apps using Vue and Nuxt.`,
          `Started programming like back in 2020 when I had nothing better to do. Ended up getting quite into it.`, 
          `Eventually came to be known by different names here and there, commonly as NeTT in internet communities.`,
        ]"
      />
    </div>
    <div class="flex flex-col items-start space-y-4 text-center">
      <div class="p-2 w-full">
        Written by
        <a href="https://github.com/retraigo" class="text-chaos-foreground">Pranev</a>
      </div>
      <div class="p-2 w-full">
        Made with <a href="https://nuxtjs.org" class="text-chaos-foreground">Nuxt 3</a>
      </div>
      <!--        <div class = "p-2">Background from <a href = "https://svgbackgrounds.com" class = "text-chaos-foreground">SVGBackgrounds.com</a></div>-->
      <div class="p-2 w-full">
        Font used -
        <a
          href="https://fonts.google.com/specimen/Montserrat"
          class="text-chaos-foreground"
          >Montserrat</a
        >
      </div>
      <div class="p-2 w-full">
        Credits to the color <span class="text-chaos-foreground">#ff00c3</span> for
        existing.
      </div>
    </div>
  </div>
</template>
<script>
definePageMeta({
  layout: "erena",
  title: "Pranev",
});
</script>