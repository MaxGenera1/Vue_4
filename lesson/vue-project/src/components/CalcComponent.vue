<template>
  <div>
    <div class="calc">
        <input class="input" type="text" v-model="result">
        <button @click="$event => addBtn(num)" v-for="num in nums" :key="num.id">{{ num }}</button>
        <button @click="addBtn(tab)" v-for="tab in tabs" :key="tab.id">{{ tab }}</button>
        <button @click="calcResult">=</button>
        <button class="reset" @click="clearResult">reset</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CalcComponent',

  data() {
    return {
      result: '',  
      nums: [1, 2, 3, 4, 5, 6, 7, 8, 9, 0],
      tabs: ['-', '+', '*', '/']
    };
  },
  methods: {
    addBtn(char) {
        this.result = this.result.toString();
        this.result += char;
    },
    calcResult() {
        this.result = eval(this.result)
    },
    clearResult() {
        this.result = '';
    }
  },
};
</script>

<style lang="css" scoped>
    .calc {
        display: grid;
        grid-template-columns: repeat(3, 70px);
        justify-content: center;
        padding: 48px 0;
    }
    .input {
        grid-column: 1 /-1;
        text-align: right;
    }
    .reset {
        grid-column: 1 /-1;
    }
</style>