<script lang="ts">
import Vue from 'vue';

interface SampleDate {
  counter: number;
  initCounter: number;
  message: {
    action: string | null;
    amount: number | null;
  };
}

export default /*#__PURE__*/Vue.extend({
  name: 'Vuenicetimeline', // vue component name
  data(): SampleDate {
    return {
      counter: 5,
      initCounter: 5,
      message: {
        action: null,
        amount: null,
      },
    };
  },
  computed: {
    changedBy() {
      const { message } = this as SampleDate;
      if (!message.action) return 'initialized';
      return `${message.action} ${message.amount || ''}`.trim();
    },
  },
  methods: {
    increment(arg: Event | number): void {
      const amount = (typeof arg !== 'number') ? 1 : arg;
      this.counter += amount;
      this.message.action = 'incremented by';
      this.message.amount = amount;
    },
    decrement(arg: Event | number): void {
      const amount = (typeof arg !== 'number') ? 1 : arg;
      this.counter -= amount;
      this.message.action = 'decremented by';
      this.message.amount = amount;
    },
    reset(): void {
      this.counter = this.initCounter;
      this.message.action = 'reset';
      this.message.amount = null;
    },
  },
});
</script>

<template>
  <div class="vuenicetimeline">
    <p>The counter was {{ changedBy }} to <b>{{ counter }}</b>.</p>
    <button @click="increment">
      Click +1
    </button>
    <button @click="decrement">
      Click -1
    </button>
    <button @click="increment(5)">
      Click +5
    </button>
    <button @click="decrement(5)">
      Click -5
    </button>
    <button @click="reset">
      Reset
    </button>
  </div>
</template>

<style scoped>
  .vuenicetimeline {
    display: block;
    width: 400px;
    margin: 25px auto;
    border: 1px solid #ccc;
    background: #eaeaea;
    text-align: center;
    padding: 25px;
  }
  .vuenicetimeline p {
    margin: 0 0 1em;
  }
</style>
