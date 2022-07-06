<template >
  <div id="app">
  <div class="grid h-screen place-items-center back h-screen overflow-hidden">
    <div class="font-bold text-base text-7xl tracking-widest rounded-lg p-10 backdrop-blur-sm bg-white/30 text-slate-200">
      <h1 class="flex justify-center">{{this.time}}</h1>
      <h3 v-if="date" class="text-2xl mt-3.5">{{dateBuilder()}}</h3>
      <pre-loader v-if="show"/>
    </div>
  </div>
  </div>

</template>

<script>
import preLoader from "@/UI/preLoader";
export default {
  components: {preLoader},
  data() {
    return{
      time: "",
      date: false,
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
        this.date = true
      }, 1000)
    },
    dateBuilder() {
      let d = new Date();
      let months = [
        "January",
        "Feruary",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December",
      ];
      let days = [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday",
      ];

      let day = days[d.getDay()];
      let date = d.getDate();
      let month = months[d.getMonth()];
      let year = d.getFullYear();

      return `${day} ${date} ${month} ${year}`;
    },
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
