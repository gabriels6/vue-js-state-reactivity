<template>
  <div id="app">
    <button @click="increment($event)">Click</button>
    {{ counter2 }}
    {{ fullNameComputed }}
  </div>
</template>

<script>

// $event -> get event
export default {
  name: 'App',
  data() {
    return {
      count: {
        x: 0,
      },
      counter2: 0,
      firstName: 'First name',
      lastName: 'Last Name',
    };
  },
  computed: {
    // computed - good for performance, if the value doesn't have to change everytime
    // you instantiate on template
    fullNameComputed() {
      return `${this.firstName} ${this.lastName}`;
    },
    fullNameObj: {
      get() {
        return `${this.firstName} ${this.lastName}`;
      },
      set(value) {
        console.log(value);
        this.firstName = 'abc';
        this.lastName = 'def';
      },
    },
  },
  methods: {
    increment(event) {
      console.log(event);
      this.counter2 += 1;
    },
  },
  mounted() { // mounted - executado após o componente ter sido montado na tela
    console.log(this.count);

    // Options to add properties into data variables

    // this.count = 2;
    // this.$set(this.count, 'y', 1);
    // this.count = { ...this.count, ...{ a: 1, b: 2 } };
  },
};
</script>

<style lang="scss">

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
