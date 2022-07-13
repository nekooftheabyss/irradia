<template>
  <div :class="`flex flex-col space-y-4 relative w-72`">
    <div
      class="
        w-full 
        h-12
        p-4
        bg-chaos-foreground
        text-gray-900 cursor-pointer
        border-maid-600 border-2
        dark:bg-chaos-primary dark:text-white
        flex flex-row
        items-center
        justify-between
      "
      @click="toggleDrop"
    >
      <span>{{ choices.find(x => x[1] === myChosen)?.[0] || "Choose" }}</span
      ><span
        :class="`transition duration-500 ease-in-out transform ${
          dropOpen ? 'rotate-180' : 'rotate-0'
        }`"
        ><SVGDown
      /></span>
    </div>
    <div
      :class="`absolute top-8 ${
        dropOpen ? 'h-48' : 'h-0'
      } w-full z-20 overflow-y-scroll transition-all duration-500 ease-in-out flex flex-col space-y-2 bg-white text-gray-900 border-maid-600 dark:bg-abyss-800 dark:text-white`"
    >
      <div
        v-for="choice in choices"
        :key="`selection_${friendlyName.replace(/\s/g, '_')}_${choice[0].replace(/\s/g, '_')}`"
        class="
          h-12
          p-4
          dark:border-maid-600
          cursor-pointer
          hover:bg-maid-200
          dark:hover:bg-maid-600
          flex flex-row
          items-center
          transition
          duration-300
          ease-in-out
        "
        @click="(x) => chooseItem(choice)"
      >
        <span> {{ choice[0] }}</span>
      </div>
    </div>
  </div>
</template>
<script setup>
const emit = defineEmits(["update"]);

const props = defineProps({
    friendlyName: {
    type: String,
    default() {
      return null;
    },
  },
  choices: {
    type: Array,
    default: null,
  },
  chosen: {
    default: null,
  },
});
const myChosen = ref(props.chosen);
const dropOpen = ref(false);

function toggleDrop() {
  dropOpen.value = !dropOpen.value;
  console.log(dropOpen.value);
}
function chooseItem(x) {
  console.log(x)
  myChosen.value = x[1];
  emit('update', myChosen.value)
  dropOpen.value = false;
}
</script>