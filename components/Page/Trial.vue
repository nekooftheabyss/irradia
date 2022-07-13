
<template>
  <div class="p-8">
    <div class="text-lg">
      <div class="
          flex
          md:flex-row md:space-x-12
          flex-col
          items-stretch
          md:justify-between
          justify-start
        ">
        <div class="py-2 w-full">
          <div class="
              p-2
              text-gray-700
              dark:text-white
              font-semibold
              border-zinc-400 border-b-2
            ">
            {{ article.name.split("-").map(s => s.charAt(0).toUpperCase() + s.slice(1).toLowerCase()).join(" ") }}
          </div>

          <div class="md:flex flex-col items-start justify-between px-2">
            <div class="flex flex-col items-start w-full md:w-auto font-semibold">
              {{article.description}}
            </div>
            <div class="flex flex-col items-start w-full">
              <div
                v-for="inputThing in article.args"
                :key="inputThing.name"
              >
                <div
                  v-if="inputThing.type === 'text'"
                  class="flex flex-col items-start space-y-4"
                ><label for="someInput">{{inputThing.description}}</label><input
                    id="someInput"
                    v-model="input.text"
                    @keyup="submitOrNah"
                    type="text"
                    class="border-chaos-primary dark:bg-chaos-primary dark:border-chaos-foreground border-2 w-full h-12 rounded-md p-2"
                  /> </div>
                <div
                  v-if="inputThing.type === 'number'"
                  class="flex flex-col items-start space-y-4"
                ><label for="someInput">{{inputThing.description}}</label><input
                    id="someInput"
                    v-model="input.number"
                    @keyup="submitOrNah"
                    type="number"
                    class="border-chaos-primary dark:bg-chaos-primary dark:border-chaos-foreground border-2 w-full h-12 rounded-md p-2"
                  /> </div>
                <div
                  v-if="inputThing.type === 'boolean'"
                  class="flex flex-col items-start space-y-4"
                ><label for="someInput">{{inputThing.description}}</label><input
                    id="someInput"
                    v-model="input.condit"
                    @keyup="submitOrNah"
                    type="checkbox"
                    class="border-chaos-primary dark:bg-chaos-primary dark:border-chaos-foreground border-2 w-full h-12 rounded-md p-2"
                  /> </div>
              </div>
              <div class="flex flex-col items-start justify-start">
                <div :class="`p-3 ${['string', 'name'].includes(article.name) ? 'break-all' : ''}`">
                 Your Result:  <span class = "font-bold">{{result ? `${["name", "character", "fantasy-name"].includes(article.name) ? result.split(" ").map(s => s.charAt(0).toUpperCase() + s.slice(1).toLowerCase()).join(" ") : result}` : `Nothing. Just like your life.`}}</span>
                </div>
                <button
                  class="p-4 bg-zinc-600 text-white rounded-lg transition duration-500 ease-in-out transform hover:translate-y-1"
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

<script>
import lala from '@nekooftheabyss/lala'
import articles from '@/data/Features'
export default {
  props: {
    modez: {
      type: String,
      default: () => 'string',
    },
  },
  data() {
    const article = articles.find((x) => x.name === this.modez)
    if (!article) this.$router.push('/')
    return {
      article,
      input: {
        text: null,
        condit: false,
        number: 5,
      },
      result: '',
    }
  },
  methods: {
    formatDate(d) {
      return new Date(d).toUTCString()
    },
    submitOrNah(e) {
      if (e.keyCode === 13) return this.getResult()
    },
    getResult() {
      this.result = lala.random[this.article.keyType]
        ? lala.random[this.article.keyType](
            this.article.name === 'fantasy-creature'
              ? true
              : this.article.args.length !== 0
              ? this.article.args[0].type === 'text'
                ? this.input.text
                : this.article.args[0].type === 'number'
                ? this.input.number
                : this.input.condit
              : null
          )
        : 'Temporary Error'
      console.log(this.result)
    },
  },
}
</script>