<template>
  <div class="flex flex-col space-y-96 lg:space-y-108 w-full mt-48 md:mt-72">
    <!-- HERO -->
    <div class="flex flex-col space-y-96 lg:space-y-108">
      <div
        ref="item1"
        class="
          text-4xl
          lg:text-6xl
          font-extrabold
          text-center text-chaos-primary
          dark:text-chaos-foreground
        "
      >
        Gaze into the abyss.
      </div>
      <div
        ref="item2"
        class="
          text-4xl
          lg:text-6xl
          font-extrabold
          text-center text-chaos-primary
          dark:text-maid-200
        "
      >
        Does the abyss really gaze back at you?
      </div>
      <div
        ref="item3"
        class="
          text-4xl
          lg:text-6xl
          font-extrabold
          text-center text-chaos-primary
          dark:text-chaos-foreground
        "
      >
        It is probably the mysterious cat that resides in it.
      </div>
      <div
        ref="item4"
        class="
          w-full
          flex flex-row
          justify-between
          items-center
          space-x-4
          opacity-70
        "
      >
        <img
          src="/eye/Neko_L.webp"
          class="w-36 md:w-72 lg:w-96 animate-pulse"
          alt="Right eye of the mysterious neko"
        />
        <img
          src="/eye/Neko_R.webp"
          class="w-36 md:w-72 lg:w-96 animate-pulse"
          alt="Left eye of the mysterious neko"
        />
      </div>
    </div>
    <div class="p-8">
      <div class="text-4xl lg:text-6xl font-extrabold text-center">
        There are five routes ahead of you.
      </div>
    </div>
    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
      <CardChoice
        title="La Lala"
        description="Generates random text."
        image="/lala.webp"
        link="/apps/la-lala"
      />
      <CardChoice
        title="Fortuna"
        description="A TS module for emulating a gacha system."
        image="/placeholder/1.png"
        link="https://github.com/queenochaos/fortuna"
      />
      <CardChoice
        title="Kuroneko"
        description="A discord bot."
        image="/queen/icon.png"
        link="/apps/queenofchaos"
      />
      <CardChoice
        title="Pranev"
        description="The dude that owns Neko Of The Abyss."
        image="/nett.png"
        link="/nett"
      />
      <CardChoice
        title="Duration"
        description="Get the formated time duration. ES Module that works in Node, Deno and browsers."
        image="/placeholder/3.png"
        link="https://github.com/retraigo/duration.js"
      />
    </div>
  </div>
</template>
<script setup>
definePageMeta({
  title: "Home",
});

/*
const item1 = ref(null);
const item2 = ref(null);
const item3 = ref(null);
const item4 = ref(null);
const items = [item1, item2, item3, item4];
const current = ref(0);

onMounted(() => {
  nextTick(function () {
    window.addEventListener("keydown", (event) => {
      console.log(event.key);
      if (event.key === " ") {
        current.value++;
        if (items[current.value]) {
          items[current.value].value.scrollIntoView({ behavior: "smooth" });
          items[current.value].value;
        }
        x;
      }
    });
  });
});
*/
</script>
