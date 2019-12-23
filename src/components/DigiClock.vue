<template>
  <div class="digiClock">
    <!--  -->
    <div class="clock-wrapper">
      <p class="date">{{ day }} {{ month }} {{ year }}</p>

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
#clock {
  text-align: center;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  color: #daf6ff;
  text-shadow: 0 0 20px rgba(10, 175, 230, 1), 0 0 20px rgba(10, 175, 230, 0);

  .time {
    letter-spacing: 0.05em;
    font-size: 80px;
    padding: 5px 0;
  }
  .date {
    letter-spacing: 0.1em;
    font-size: 24px;
  }
  .text {
    letter-spacing: 0.1em;
    font-size: 12px;
    padding: 20px 0 0;
  }
}
</style>
