<template>
  <div class="NewCalculator">
    {{ msg }}

    <div class="display">
      <input v-model.number="operand1" />
      <input v-model.number="operand2" />
    </div>
    <div class="keyboard">
      <button @click="result = operand1 + operand2">+</button>
      <button @click="result = operand1 - operand2">-</button>
      <button @click="result = operand1 * operand2">*</button>
      <button @click="result = operand1 ** operand2">**</button>
      <button v-if="operand2 != 0" @click="result = operand1 / operand2">
        /
      </button>
      <button
        v-if="operand2 != 0"
        @click="result = Math.floor(operand1 / operand2)"
      >
        //
      </button>
    </div>
    <div class="result">
      <strong>Result:{{ result }}</strong>
    </div>
  </div>
</template>

<script>
export default {
  name: "NewCalculator",
  props: {
    msg: String,
  },
  data() {
    return {
      operand1: 0,
      operand2: 0,
      result: 0,
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

input {
  width: 100px;
  height: 100px;
  font-size: 30px;
}
.display {
  font-size: 30px;
  display: flex;
  justify-content: center;
  align-items: center;
}
button {
  width: 50px;
  height: 50px;
  font-size: 30px;
}
.keyboard {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 50px;
}
.result {
  font-size: 30px;
  margin-top: 30px;
}
</style>
