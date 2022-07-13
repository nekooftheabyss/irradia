<template>
<div class = "flex flex-col">
    <h1 class = "text-4xl font-bold w-full text-center">Postulates of the Abyss</h1>
    <ul class = "py-8 px-2 flex flex-col items-center text-left w-full space-y-8 list-disc">
        <li v-for = "postulate in Postulates" :key="postulate.message" class = "ml-12 w-full font-semibold odd:text-maid-600 even:text-maid-500 dark:odd:text-chaos-foreground dark:even:text-maid-200">
            {{postulate.message}}
        </li>
    </ul>
</div>
</template>

<script setup>
import Postulates from "@/data/Postulates.js"
definePageMeta({
  title: "Postulates",
});
</script>