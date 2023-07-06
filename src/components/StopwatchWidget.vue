<template>
  <div class="stopwatch-container">
    <h2 class="header">Penghitung Detik</h2>
    <div class="stopwatch">
      <p>{{ formatTime }}</p>
      <div class="controls">
        <button @click="start" :disabled="isRunning" class="button-primary">Start</button>
        <button @click="stop" :disabled="!isRunning" class="button-secondary">Stop</button>
        <button @click="reset" :disabled="isRunning" class="button-tertiary">Reset</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isRunning: false,
      elapsedTime: 0,
      startTime: null,
    };
  },
  computed: {
    formatTime() {
      const minutes = Math.floor(this.elapsedTime / 60000);
      const seconds = Math.floor((this.elapsedTime % 60000) / 1000);
      const milliseconds = Math.floor((this.elapsedTime % 1000) / 10);

      return `${this.padTime(minutes)}:${this.padTime(seconds)}:${this.padTime(
        milliseconds
      )}`;
    },
  },
  methods: {
    padTime(time) {
      return time.toString().padStart(2, '0');
    },
    start() {
      if (!this.isRunning) {
        this.startTime = Date.now() - this.elapsedTime;
        this.isRunning = true;
        this.timer = setInterval(() => {
          this.elapsedTime = Date.now() - this.startTime;
        }, 10);
      }
    },
    stop() {
      if (this.isRunning) {
        clearInterval(this.timer);
        this.isRunning = false;
      }
    },
    reset() {
      this.stop();
      this.elapsedTime = 0;
    },
  },
};
</script>

<style scoped>
.header {
  display:inline-block;
  background-color: rgba(255, 255, 255, 0.1);
  
  padding: 4px 9px;
  border-radius: 4px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
  color: rgb(0, 0, 0);
}

.header {
  margin: 4px 3px 12px;
  color: rgb(197, 231, 0);
}
.stopwatch-container {
  
  background-color: #929292;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.stopwatch {
  text-align: center;
}

.stopwatch p {
  font-size: 24px;
  margin: 0;
  color: white;
}

.stopwatch .controls {
  margin-top: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.stopwatch .controls button {
  padding: 10px 20px;
  margin: 0 9px;
  font-size: 16px;
  border-radius: 4px;
  border: none;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2)}

.stopwatch .controls button.button-primary {
  background-color: #4caf50;
  color: white;
}

.stopwatch .controls button.button-secondary {
  background-color: #f44336;
  color: white;
}

.stopwatch .controls button.button-tertiary {
  background-color: #2196f3;
  color: white;
}

.stopwatch .controls button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

.stopwatch .controls button:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px8px rgba(0, 0, 0, 0.2);
}

.stopwatch .controls button:active {
  transform: translateY(0);
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}
</style>
