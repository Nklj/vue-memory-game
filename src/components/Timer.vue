<template>
  <span>{{ value }}</span>
</template>

<script>
export default {
  props: ["disabled"],
  data: () => ({
    startTime: 0,
    currentTime: 0,
    timerId: null,
  }),
  computed: {
    value() {
      return this.humanizeTime(this.currentTime - this.startTime);
    },
  },
  watch: {
    disabled: {
      immediate: true,
      handler: "resetTimer",
    },
  },
  methods: {
    humanizeTime(durationInMs) {
      const duration = durationInMs / 1000;
      const time = [
        Math.floor(duration / 3600),
        parseInt((duration / 60) % 60),
        parseInt(duration % 60),
      ];
      time.forEach((part, index) => {
        time[index] = part < 10 ? `0${part}` : part;
      });
      return time.join(":");
    },

    restart() {
      clearInterval(this.timerId);
      this.startTime = Date.now();
      this.currentTime = this.startTime;
      this.timerId = setInterval(() => (this.currentTime = Date.now()), 1000);
    },

    resetTimer(disabled) {
      if (!disabled) {
        this.restart();
      } else {
        clearInterval(this.timerId);
      }
    },
  },
};
</script>


