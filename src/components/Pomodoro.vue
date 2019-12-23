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
          <!--     Start TImer -->
          <vs-button radius color="#000" type="gradient" 
            id="start"
            class=""
            v-if="!timer"
            @click="startTimer"
          >
            <vs-icon  icon="play_circle_outline" color="#124"></vs-icon>

          </vs-button>
          <!--     Pause Timer -->
          <vs-button radius color="#fff" type="gradient" 
            id="stop"
            class=""
            v-if="timer"
            @click="stopTimer"
          >
            <vs-icon icon="pause_circle_outline" color="#124"></vs-icon>
          </vs-button>
          <!--     Restart Timer -->
          <vs-button radius color="#000" type="gradient" 
            id="reset"
            class=""
            v-if="resetButton"
            @click="resetTimer"
          >
            <vs-icon icon="undo" color="#124"></vs-icon>
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
      title: "Let the countdown begin!!"
    };
  },
  // ========================
  methods: {
    startTimer: function() {
      this.timer = setInterval(() => this.countdown(), 1000);
      this.resetButton = true;
      this.title = "Greatness is within sight!!"
    },
    stopTimer: function() {
      clearInterval(this.timer);
      this.timer = null;
      this.resetButton = true;
      this.title = "Never quit, keep going!!"
    },
    resetTimer: function() {
      this.totalTime = (25 * 60);
      clearInterval(this.timer);
      this.timer = null;
      this.resetButton = false;
      this.title = "Let the countdown begin!!"
    },
    padTime: function(time) {
      return (time < 10 ? '0' : '') + time;
    },
    countdown: function() {
      if(this.totalTime >= 1){
        this.totalTime--;
      } else{
        this.totalTime = 0;
        this.resetTimer()
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
      const seconds = this.totalTime - (this.minutes * 60);
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
