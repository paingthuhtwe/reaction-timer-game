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
  <div v-if="isPlaying">
    <BlogPage :delay="delay" @click="stop" />
  </div>
</template>

<script>
import BlogPage from "./components/BlogPage.vue";
export default {
  name: "App",
  data() {
    return {
      isPlaying: false,
      delay: null,
    };
  },
  methods: {
    start() {
      this.isPlaying = !this.isPlaying;
      this.delay = 2000 + Math.random() * 5000;
    },
    stop() {
      this.isPlaying = !this.isPlaying;
    },
  },
  components: {
    BlogPage,
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
