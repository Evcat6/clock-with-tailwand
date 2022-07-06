<template >
  <div id="app">
  <div class="grid h-screen place-items-center back h-screen overflow-hidden">
    <div class="font-bold text-base text-7xl tracking-widest rounded-lg p-10 backdrop-blur-sm bg-white/30 text-slate-200">
      <h1>{{time}}</h1>
      <div
          v-if="show"
          style="border-top-color:transparent"
          class="w-16 h-16 border-4 border-slate-200 border-dashed rounded-full animate-spin"
      ></div>
    </div>
  </div>
  </div>

</template>

<script>
export default {
  data() {
    return{
      time: "",
      show: true,
    }
  },
  methods: {
    getTime() {
      setInterval(() => { this.time = new Date().toLocaleTimeString()}, 1000)
},
    showToggle() {
      setTimeout(() => {
        this.show = false
      }, 1000)
    }
  },

  mounted() {
    this.getTime()
    this.showToggle()
  }
}
</script>

<style>
.back {
  background-color: #74EBD5;
  background-image: linear-gradient(90deg, #74EBD5 0%, #9FACE6 100%);
}

</style>
