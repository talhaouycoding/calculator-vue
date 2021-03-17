<template>
  <div class="container">
    <div class="result">{{ result === "" ? 0 : result }}</div>
    <div class="btn" @click="clear">C</div>
    <div class="btn" @click="minusPlus">+/-</div>
    <div class="btn" @click="append('%')">%</div>
    <div class="btn" @click="append('/')">/</div>
    <div class="btn" @click="append('7')">7</div>
    <div class="btn" @click="append('8')">8</div>
    <div class="btn" @click="append('9')">9</div>
    <div class="btn" @click="append('x')">x</div>
    <div class="btn" @click="append('4')">4</div>
    <div class="btn" @click="append('5')">5</div>
    <div class="btn" @click="append('6')">6</div>
    <div class="btn" @click="append('-')">-</div>
    <div class="btn" @click="append('1')">1</div>
    <div class="btn" @click="append('2')">2</div>
    <div class="btn" @click="append('3')">3</div>
    <div class="btn" @click="append('+')">+</div>
    <div class="btn" @click="append('0')">0</div>
    <div class="btn" @click="comma">.</div>
    <div class="btn equal" @click="equal">=</div>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data() {
    return {
      result: '',
      operator: '',
      firstNumber: '',
      secondNumber: '',
      operators: ["+", "-", "/", "%", "x"],
    };
  },
  methods: {
    append(value) {
      if (!this.operators.includes(value)) {
        this.result += value;
      } else if (this.operators.includes(value) && this.result !== "") {
        this.operator = value;
        this.firstNumber = this.result;
        this.result = "";
      }
    },
    equal() {
      this.secondNumber = this.result;
      switch (this.operator) {
        case "+":
          this.result = +this.firstNumber + +this.secondNumber;
          break;
        case "-":
          this.result = +this.firstNumber - +this.secondNumber;
          break;
        case "x":
          this.result = +this.firstNumber * +this.secondNumber;
          break;
        case "/":
          if (this.secondNumber === "0") {
            this.result = "divide by zero";
          } else {
            this.result = +this.firstNumber / +this.secondNumber;
          }

          break;
        case "%":
          this.result = +this.firstNumber % +this.secondNumber;
          break;
      }
    },
    comma() {
      if (this.result.indexOf(".") === -1 && this.result.length > 0) {
        this.result += ".";
      }
    },
    clear() {
      this.result = "";
    },
    minusPlus() {
      if (+this.result[0] !== "-") {
        this.result = -+this.result;
      }
    },
  },
};
</script>

<style>
.container {
  background-color: lightblue;
  display: grid;
  grid-template-columns: repeat(4, 80px);
  grid-template-rows: repeat(6, 80px);
  border-radius: 20px;
}
.btn {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 1.6rem;
  font-weight: 500;
  color: #fff;
  transition: background 0.5s ease-in-out;
}
.btn:hover {
  cursor: pointer;
  background-color: rgba(116, 179, 201, 0.5);
  border-radius: 5px;
}

.result {
  grid-column: 1/-1;
  padding: 20px;
  background-color: rgba(0, 0, 0, 0.6);
  color: #fff;
  text-align: right;
  font-size: 2rem;
  border-top-right-radius: 20px;
  border-top-left-radius: 20px;
}
.equal {
  background-color: rgb(50, 125, 155);
  grid-column: 3/-1;
}
</style>
