<template>
  <div class="hello">
    <input type="number" v-model="value">
    <h5>Result: {{ result }}</h5>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      value: 0,
      result: 0,
      map: {
        M: 1000,
        CM: 900,
        D: 500,
        CD: 400,
        C: 100,
        XC: 90,
        L: 50,
        XL: 40,
        X: 10,
        IX: 9,
        V: 5,
        IV: 4,
        I: 1,
      }
    }
  },

  watch: {
    'value': {
      handler() {
        this.check(this.value);
      }
    }
  },

  methods: {
    check(num, result = '') {
      for (const key in this.map) {
        if (num >= this.map[key]) {
          if (num !== 0) {
            return this.check(num - this.map[key], result + key);
          }
        }
      }
      this.result = result;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
