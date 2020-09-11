<template>
  <div class="counter">
    <div class="counter_container">
      <div class="counter_item">
        <span>{{ days }}</span>
        <span class="item_name">days</span>
      </div>
      <span>:</span>
      <div class="counter_item">
        <span>{{ hr }}</span>
        <span class="item_name">hours</span>
      </div>
      <span>:</span>
      <div class="counter_item">
        <span>{{ min }}</span>
        <span class="item_name">min</span>
      </div>
      <span>:</span>
      <div class="counter_item">
        <span>{{ sec }}</span>
        <span class="item_name">sec</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      days: 0,
      hr: 0,
      min: 0,
      sec: 0,
    };
  },
  computed: {
    _sec: () => 1000,
    _min() {
      return this._sec * 60;
    },
    _hr() {
      return this._min * 60;
    },
    _days() {
      return this._hr * 24;
    },
  },
  mounted() {
    this.showTime();
  },
  methods: {
    formatTime(num) {
      return num < 10 ? "0" + num : num;
    },
    showTime() {
      const timer = setInterval(() => {
        const now = new Date();

        const end = new Date(2021, 5, 24, 10, 30, 60, 100);

        const dist = end.getTime() - now.getTime();

        if (dist < 0) {
          clearInterval(timer);
          alert("The countdown is down");
        }

        const days = Math.floor(dist / this._days);
        const hr = Math.floor((dist % this._days) / this._hr);
        const min = Math.floor((dist % this._hr) / this._min);
        const sec = Math.floor((dist % this._min) / this._sec);

        this.sec = this.formatTime(sec);
        this.min = this.formatTime(min);
        this.hr = this.formatTime(hr);
        this.days = this.formatTime(days);
      }, 1000);
    },
  },
};
</script>

<style lang="scss" scoped>
.counter {
  font-size: 2rem;
  color: purple;
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

.counter_container {
  display: flex;
  width: 25%;
}

.counter_item {
  display: flex;
  flex-direction: column;
  align-items: center;
  flex: 1;
}
.item_name {
  font-size: 1rem;
}

@media (min-width: 100px) and (max-width: 900px) {
  .counter_container {
    width: 100%;
  }
}
</style>
