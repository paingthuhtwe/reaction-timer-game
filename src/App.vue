<template>
  <h1 class="text-center font-bold text-4xl text-sky-800 select-none">
    How fast can you catch me?
  </h1>
  <button
    class="bg-blue-500 px-4 py-1.5 font-semibold text-slate-100 text-xl mt-9 rounded-md enabled:hover:bg-blue-600 disabled:opacity-75"
    @click="start"
    :disabled="isPlaying"
  >
    Play
  </button>
  <div v-if="result" class="mt-9">
    <ResultPage :result="result" :score="score" :closeTime="closeTime" />
  </div>
  <div v-if="isPlaying">
    <BlogPage
      :delay="delay"
      @stop="stop"
      @timer="timer"
      @showResult="showResult"
    />
  </div>
</template>

<script>
import BlogPage from "./components/BlogPage.vue";
import ResultPage from "./components/ResultPage.vue";
export default {
  name: "App",
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: 0,
      result: null,
      time: null,
      closeTime: 5,
      close: null,
    };
  },
  methods: {
    start() {
      this.isPlaying = !this.isPlaying;
      this.delay = 2000 + Math.random() * 5000;
      this.result = null;
      this.score = 0;
    },
    stop() {
      this.isPlaying = !this.isPlaying;
    },
    timer() {
      this.time = setInterval(() => {
        this.score += 100;
      }, 100);
    },
    showResult() {
      clearInterval(this.time);
      if (this.score < 1000) {
        this.result = "Nice Guys, you're too fast!";
      } else if ((this.score > 1000) & (this.score < 2000)) {
        this.result = "Good Luck next time!";
      } else {
        this.result = "Your are too slow!";
      }
      this.close = setInterval(() => {
        this.closeTime -= 1;
        if (this.closeTime === 0) {
          clearInterval(this.close);
          this.closeTime = 5;
          this.result = null;
        }
      }, 1000);
    },
  },
  components: {
    BlogPage,
    ResultPage,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
