<template>
  <div class="NewCalculator">
    {{ msg }}

    <div class="display">
      <div class="input container">
        <input class="input__left" v-model.number="operand1" />
        <input class="input__right" v-model.number="operand2" />
      </div>
      <div class="radio container">
        <input
          class="radio__left"
          type="radio"
          value="1"
          name="operand"
          checked
        />
        <input class="radio__right" type="radio" value="2" name="operand" />
      </div>
    </div>
    <div class="keyboard">
      <div class="operations">
        <button @click="result = +operand1 + +operand2">+</button>
        <button @click="result = operand1 - operand2">-</button>
        <button @click="result = operand1 * operand2">*</button>
        <button @click="result = operand1 ** operand2">**</button>
        <button
          v-if="operand2 == 0"
          disabled
          @click="result = operand1 / operand2"
        >
          /
        </button>
        <button v-else @click="result = operand1 / operand2">/</button>
        <button
          class="number"
          v-if="operand2 == 0"
          disabled
          @click="result = Math.floor(operand1 / operand2)"
        >
          //
        </button>
        <button
          class="number"
          v-else
          @click="result = Math.floor(operand1 / operand2)"
        >
          //
        </button>
      </div>
      <div class="number">
        <button
          @click="checked($event)"
          v-for="item in numberkey"
          :key="item.id"
        >
          {{ item }}
        </button>
        <button @click=" delet()" style="width: 100px">delete</button>
      </div>
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
      numberkey: [1, 2, 3, 4, 5, 6, 7, 8, 9, 0],
    };
  },
  methods: {
    checked(event) {
      if (document.querySelector(".radio__left").checked) {
        this.operand1 += event.target.innerText;
      } else {
        this.operand2 += event.target.innerText;
      }
    },
    delet() {
      if (document.querySelector(".radio__left").checked) {
        this.operand1 = document.querySelector(".input__left").value.slice(0,-1)
      } else {
        this.operand2 = document.querySelector(".input__right").value.slice(0,-1)
      }
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  padding: 0;
  margin: 0;
}
.container {
  width: 600px;
  margin: 0 auto;
}
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
  flex-direction: column;
  align-items: center;
}
.display div {
  display: flex;
  justify-content: space-evenly;
}
.radio input {
  width: 20px;
}
button {
  width: 50px;
  height: 50px;
  font-size: 30px;
}
.keyboard div {
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
