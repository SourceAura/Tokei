<template>
  <div class="home">
    <div class="container"></div>
    <!-- brand logo here later -->
    <!-- <img alt="Vue logo" src="../assets/logo.png" /> -->
    
    <vs-tabs class="container" value='1' alignment="center">
      <vs-tab label="Alarms:">
        <div>
          <Alarm msg="" />
        </div>
      </vs-tab>
      <vs-tab active label="Current:">
        <div>
          <DigiClock msg="" />
        </div>
      </vs-tab>
      <vs-tab label="Pomodoro:">
        <div>
          <Pomodoro msg="" />
        </div>
      </vs-tab>
      
    </vs-tabs>
  </div>
</template>

<script>
// @ is an alias to /src
import Alarm from "@/components/Alarm.vue";
import DigiClock from "@/components/DigiClock.vue";
import Pomodoro from "@/components/Pomodoro.vue";

export default {
  name: "home",
  components: {
    Alarm,
    DigiClock,
    Pomodoro
  }
};
</script>

<style lang="css">
  body {
    text-align:center;
  }
  .container {
    margin-top: 40px;
  }
</style>
