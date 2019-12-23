<template>
  <div class="digiClock">
    <div class="clock-cup">
      <!-- date -->
      <p class="date">{{ day }} {{ month }} {{ year }}</p>
      <!-- divider maybe? -->
      <!-- digital clock -->
      <div class="clock">
        <h1 class="time">{{ hours }}:{{ minutes }}:{{ seconds }}</h1>
      </div>
    </div>
    <!--  -->
  </div>
</template>

<script>
import moment from "moment";

moment.locale("en");

export default {
  created() {
    setInterval(() => {
      this.time = moment();
    }, 1000);
  },
  data() {
    return {
      time: moment()
    };
  },
  computed: {
    seconds() {
      return moment(this.time).format("ss");
    },
    minutes() {
      return moment(this.time).format("mm");
    },
    hours() {
      return moment(this.time).format("HH");
    },
    day() {
      return moment(this.time).format("DD");
    },
    month() {
      return moment(this.time).format("MMM");
    },
    year() {
      return moment(this.time).format("YYYY");
    }
  }
};
</script>

<style lang="css">
html,
body {
  height: 100%;
}
h1 {
  color: whitesmoke;
}
p {
  margin: 0;
  padding: 0;
  color: whitesmoke;
  font-family: "Dosis", cursive !important;
}
</style>
