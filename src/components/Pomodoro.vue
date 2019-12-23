<template>
  <section id="app" class="hero is-info is-fullheight is-bold">
    <div class="hero-body">
      <div class="container has-text-centered">
        <h2 class="title is-6">{{ title }}</h2>

        <div id="timer">
          <span id="minutes">{{ minutes }}</span>
          <span id="middle">:</span>
          <span id="seconds">{{ seconds }}</span>
        </div>

        <div id="buttons">
          <!-- Start TImer -->
          <vs-button
            v-if="!timer"
            type="line"
            @click="startTimer"
            class="btn"
            color=""
          >
            <vs-icon size="small" icon="play_circle_outline" color=""></vs-icon>
          </vs-button>

          <!-- Pause Timer -->
          <vs-button
            v-if="timer"
            type="line"
            @click="stopTimer"
            class="btn"
            color=""
          >
            <vs-icon
              size="small"
              icon="pause_circle_outline"
              color=""
            ></vs-icon>
          </vs-button>
          <!--     Restart Timer -->
          <vs-button
            v-if="resetButton"
            type="line"
            @click="resetTimer"
            class="btn"
            color=""
          >
            <vs-icon size="small" icon="undo" color=""></vs-icon>
          </vs-button>
        </div>
      </div>
    </div>
  </section>
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
  // ========================
  data() {
    return {
      timer: null,
      totalTime: 25 * 60,
      resetButton: false,
      title: "...one step at a time."
    };
  },
  // ========================
  methods: {
    startTimer: function() {
      this.timer = setInterval(() => this.countdown(), 1000);
      this.resetButton = true;
      this.title = "...focus.";
    },
    stopTimer: function() {
      clearInterval(this.timer);
      this.timer = null;
      this.resetButton = true;
      this.title = "...remember, not to forget.";
    },
    resetTimer: function() {
      this.totalTime = 25 * 60;
      clearInterval(this.timer);
      this.timer = null;
      this.resetButton = false;
      this.title = "...";
    },
    padTime: function(time) {
      return (time < 10 ? "0" : "") + time;
    },
    countdown: function() {
      if (this.totalTime >= 1) {
        this.totalTime--;
      } else {
        this.totalTime = 0;
        this.resetTimer();
      }
    }
  },
  // ========================
  computed: {
    minutes: function() {
      const minutes = Math.floor(this.totalTime / 60);
      return this.padTime(minutes);
    },
    seconds: function() {
      const seconds = this.totalTime - this.minutes * 60;
      return this.padTime(seconds);
    }
  }
};
</script>

<style lang="css">
@import url(https://fonts.googleapis.com/css?family=Dosis);

#message {
  color: #ddd;
  font-size: 50px;
  margin-bottom: 20px;
}

#timer {
  font-size: 200px;
  line-height: 1;
  margin-bottom: 40px;
}
</style>
