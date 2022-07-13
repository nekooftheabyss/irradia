
<template>
  <footer class="bg-none dark:bg-chaos-primary text-chaos-primary dark:text-white shadow-md text-center md:text-left">
    <div
      class="
        sm:flex
        items-center
        justify-between
        max-w-6xl
        mx-auto
        py-4
        px-4 space-y-4 md:space-y-0 md:space-x-4
        md:px-8
        text-sm
      "
    >
      <div class="flex-1 space-y-4 md:space-y-0 md:space-x-4">
        <span>
          Copyright
          <a
            href="https://github.com/retraigo"
            target="_blank"
            class="font-bold text-chaos-tertiary dark:text-chaos-foreground"
          >
            NeTT
          </a>
        </span>
        <div
          class="
            font-bold
            flex flex-row
            items-center
            fill-transparent flex justify-center
            stroke-chaos-primary dark:stroke-chaos-foreground stroke-2
            cursor-pointer
            space-x-4
          "
          @click="toggleDark"
        >
          <span>Make It {{ isDark ? "Bright" : "Dark" }}</span>
          <SVGSun v-show="isDark" />
          <SVGMoon v-show="!isDark" />
        </div>
      </div>
      <div class="flex-initial mt-3 sm:mt-0 dark:text-chaos-foreground">
        <a
          href="https://nekooftheabyss.moe"
          target="_blank"
          class="font-semibold"
        >
          Neko of the Abyss
        </a>
      </div>
    </div>
  </footer>
</template>



<script setup>
import { useMainConfig } from "@/store/mainconfig.js";

const mainConfig = useMainConfig();

let isDark = computed(() => mainConfig.darkMode);
function toggleDark() {
  mainConfig.switch();
  console.log(mainConfig.darkMode);
}
</script>