<template>
  <div class="p-8">
    <div class="text-lg">
      <div
        class="
          flex
          md:flex-row md:space-x-12
          flex-col
          items-stretch
          md:justify-between
          justify-start
        "
      >
        <div class="py-2 w-full">
          <div
            class="
              p-2
              text-gray-700
              dark:text-white
              font-semibold
              border-gray-400 border-b-2
            "
          >
            Some Random Text Generators:
          </div>
          <div
            class="
              md:flex
              flex-row
              justify-between
              items-start
              space-y-4
              md:space-y-0 md:space-x-4
            "
          >
            <div
              class="
                flex flex-col
                items-center
                w-full
                p-4
                space-y-24
                order-2
                md:order-1
              "
            >
            <div class = "font-semibold">Choose a function from the dropdown!</div>
              <FormPicker
                friendly-name="Lala Features"
                :choices="
                  articles.map((x) => [lala.capitalize(x.name.replace('-', ' '), true), x.keyType])
                "
                :chosen = "mode"
                @update="setMode"
              />
              <LalaMode :mode="mode" :key="mode" />
            </div>
          </div>
          <div class="p-4">
            Lala is a collection of random useful (probably) javascript classes
            and functions. I compiled them into a web app for easy use. Lala is
            licensed under the MIT license. Please refer to
            <a
              href="https://github.com/retraigo/lala/blob/main/LICENSE"
              target="_blank"
              class="text-chaos-foreground"
              >the license</a
            >
            for information about copyright.
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import articles from "@/data/Features";
import * as lala from "@nekooftheabyss/lala";
const enabled = ref(false);
const mode = ref(articles[0].keyType);
definePageMeta({
  title: "Lala",
  description:
    "A collection of random useful (probably) javascript classes and functions.",
});

function formatDate(d) {
  return new Date(d).toUTCString();
}
function setMode(s) {
  mode.value = s
}
</script>

