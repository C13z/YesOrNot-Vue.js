<template>
  <h2>{{ customTitle }}</h2>
  <p>{{ counter }} <sup>2</sup> = {{ squareCounter }}</p>
  <p data-testid="counter">{{ counter }}</p>

  <div class="buttons-container">
    <button @click="increase">+1</button>
    <button @click="decrease">-1</button>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    start: {
      type: Number,
      default: 100,
    },
    validator(value) {
      return value >= 0;
    },
  },
  data() {
    return {
      counter: this.start,
    };
  },
  methods: {
    // getSquareValue() {
    //   return this.counter * this.counter;
    // },
    increase() {
      this.counter = this.counter + 1;
    },
    decrease() {
      this.counter--;
    },
  },
  computed: {
    squareCounter() {
      return this.counter * this.counter;
    },
    customTitle() {
      return this.title || "Counter";
    },
  },
};
</script>

<style>
button {
  background-color: #64b687;
  border-radius: 5px;
  color: white;
  border: 1px solid white;
  margin: 0 5px;
  padding: 5px 15px;
  transition: 0.3s ease-in-out;
}
</style>