
<template>
  <div class="p-8 w-full">
    <div class="text-lg text-center">
      <div
        class="
          flex
          md:flex-row md:space-x-12
          flex-col
          items-center
          md:justify-between
          justify-start
        "
      >
        <div class="py-2 w-full">

          <div class="md:flex flex-col items-center justify-between px-2 space-y-8">
            <div
              class="flex flex-col items-center w-full md:w-auto font-bold text-lg"
            >
              {{ article.description }}
            </div>
            <span class="text-sm"
              >Use the "Try It" button or the spacebar key to roll a different
              result.</span
            >
            <div class="flex flex-col items-center space-y-8 mx-auto w-full">
              <div v-for="inputThing in article.args" :key="inputThing.name">
                <div
                  v-if="inputThing.type === 'text'"
                  class="flex flex-col items-start space-y-4"
                >
                  <label for="someInput">{{ inputThing.description }}</label
                  ><input
                    id="someInput"
                    v-model="input.text"
                    @keyup="submitOrNah"
                    type="text"
                    class="
                      border-chaos-primary
                      dark:bg-chaos-primary dark:border-chaos-foreground
                      border-2
                      w-full
                      h-12
                      rounded-md
                      p-2
                    "
                  />
                </div>
                <div
                  v-if="inputThing.type === 'number'"
                  class="flex flex-col items-start space-y-4"
                >
                  <label for="someInput">{{ inputThing.description }}</label
                  ><input
                    id="someInput"
                    v-model="input.number"
                    @keyup="submitOrNah"
                    type="number"
                    class="
                      border-chaos-primary
                      dark:bg-chaos-primary dark:border-chaos-foreground
                      border-2
                      w-full
                      h-12
                      rounded-md
                      p-2
                    "
                  />
                </div>
                <div
                  v-if="inputThing.type === 'boolean'"
                  class="flex flex-row items-center space-x-4"
                >
                <FormLabel type="checkbox" :friendly-name="inputThing.description" />
                  <FormCheckbox :caption="inputThing.description" @update = "(x) => input.condit = x" />
                </div>
              </div>
              <div class="flex flex-col items-center justify-start">
                <div
                  :class="`p-3 flex flex-col space-y-8 ${
                    ['string', 'name'].includes(article.name) ? 'break-all' : ''
                  }`"
                >
                  <span class = "text-center">Your Result:</span>
                  <div class="font-bold text-center">{{
                    result
                      ? `${
                          ["name", "character", "fantasy-name"].includes(
                            article.name
                          )
                            ? result
                                .split(" ")
                                .map(
                                  (s) =>
                                    s.charAt(0).toUpperCase() +
                                    s.slice(1).toLowerCase()
                                )
                                .join(" ")
                            : article.keyType === "generateRace" ? result.description : result
                        }`
                      : `Nothing. Just like your life.`
                  }}</div>
                </div>
                <button
                  class="
                    py-2 px-4
                    bg-abyss-800
                    border-2
                    border-maid-600
                    text-white
                    rounded-lg
                    transition
                    duration-500
                    ease-in-out
                    transform
                    hover:translate-y-1
                  "
                  accesskey="32"
                  @click="getResult"
                >
                  Try it!
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import * as lala from "@nekooftheabyss/lala";
import articles from "@/data/Features";

definePageMeta({
  title: "Lala",
  description:
    "A collection of random useful (probably) javascript classes and functions.",
});

const {mode} = defineProps(["mode"]);
const article = articles.find((x) => x.keyType === mode);
const input = ref({
  text: null,
  condit: false,
  number: 5,
});
let result = ref(null);

function formatDate(d) {
  return new Date(d).toUTCString();
}
function submitOrNah(e) {
  if (e.keyCode === 13) return getResult();
}
function getResult() {
  result.value = lala[article.keyType]
    ? lala[article.keyType](
        article.args.length !== 0
          ? article.args[0].type === "text"
            ? input.value.text
            : article.args[0].type === "number"
            ? input.value.number
            : input.value.condit
          : null
      )
    : "Temporary Error";
}
</script>