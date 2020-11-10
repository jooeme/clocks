<template>
  <main class="date" v-if="hours && minutes">
    <span>{{ hours }}</span>
    <div class="dots"></div>
    <span>{{ minutes }}</span>
  </main>
  <div class="line"></div>
</template>

<script>
export default {
  name: 'Clocks',
  props: {
    msg: String
  },
  data() {
    return {
      hours: '',
      minutes: ''
    };
  },
  mounted() {
    setInterval(() => {
      let myDate = new Date();
      let year = myDate.getFullYear();
      let month = myDate.getMonth() + 1;
      let date = myDate.getDate();
      let hours = myDate.getHours();
      let minutes = myDate.getMinutes();
      let seconds = myDate.getSeconds();

      if (hours < 10) {
        hours = '0' + hours;
      }
      if (minutes < 10) {
        minutes = '0' + minutes;
      }
      if (seconds < 10) {
        seconds = '0' + seconds;
      }

      //时间拼接
      this.hours = hours;
      this.minutes = minutes;
    }, 1000);
  }
};
</script>
<style scoped>
.date {
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  color: rgba(255, 255, 255, 0.8);
}
.date span {
  display: flex;
  justify-content: center;
  align-items: center;
  background: rgba(44, 44, 44, 0.444);
  border-radius: 2vw;
  padding: 1vw 2vw;
  font-family: 'JetBrains Mono';
  font-size: 444px;
  font-weight: 700;
}
.line {
  position: fixed;
  top: 50%;
  left: 0;
  width: 100%;
  height: 5px;
  background: #000;
  transform: translate(0, -50%);
}
.dots {
  display: flex;
  flex-direction: column;
  background: #000;
}
.dots::after,
.dots::before {
  content: '';
  display: inline-block;
  width: 24px;
  height: 24px;
  background: white;
  border-radius: 50%;
  margin: 30px 30px;
  animation: blink 1s infinite;
}
@keyframes blink {
  from {
    background-color: #000;
  }
  50% {
    background-color: #fff;
  }
  to {
    background-color: #000;
  }
}
</style>
