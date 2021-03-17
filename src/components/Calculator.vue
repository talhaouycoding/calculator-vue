<template>
  <div class="container">
    <div class="result">{{result}}</div>
    <div class="btn">C</div>
    <div class="btn">()</div>
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
    <div class="btn">+/-</div>
    <div class="btn" @click="append('0')">0</div>
    <div class="btn" @click="append('.')">.</div>
    <div class="btn equal" @click="equal"> = </div>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data() {
    return {
        result: '0',
        operator: '',
        secondNumber: '',
        operators:['+','-','/','%','x']
    }
  },
  methods:{
      append(value){
          if(!this.operators.includes(value)){
              this.result +=value
          }else if(this.operators.includes(value) && this.result !== ''){
              this.operator = value
              this.secondNumber = this.result
          }
            //comma test
       if(this.result.indexOf('.') !== -1 && value === '.'){
           this.result += '.';
       }

         
      },
      equal(){

      }
  }
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
  border: 1px solid #333;
  font-size: 1.5rem;
  font-weight: 500;
  color: #fff;
}
.btn:hover{
    cursor:pointer;
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
}
</style>
