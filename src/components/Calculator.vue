<template>

  <div class="calculator">
    <div class="title">Basic Calculator using VueJS</div>
    <div class="display">{{current || '0'}}</div>
    <div @click="clear" class="btn">A/C</div>
    <div @click="sign" class="btn">+/-</div>
    <div @click="percent" class="btn">%</div>
    <div @click="divide" class="btn operator">÷</div>
    <div @click="append('7')" class="btn">7</div>
    <div @click="append('8')" class="btn">8</div>
    <div @click="append('9')" class="btn">9</div>
    <div @click="multiply" class="btn operator">x</div>
    <div @click="append('4')" class="btn">4</div>
    <div @click="append('5')" class="btn">5</div>
    <div @click="append('6')" class="btn">6</div>
    <div @click="subtract" class="btn operator">-</div>
    <div @click="append('1')" class="btn">1</div>
    <div @click="append('2')" class="btn">2</div>
    <div @click="append('3')" class="btn">3</div>
    <div @click="add" class="btn operator">+</div>
    <div @click="append('0')" class="btn zero">0</div>
    <div @click="dot" class="btn">.</div>
    <div @click="equal" class="btn operator">=</div>
  </div>

</template>

<script>
export default {
  data() {
    return {
      current: '',
      operator: null,
      previous: null,
      operatorClicked: false,
    }
  },
  methods: {
    clear() {
      this.current='';
    },
    sign() {
      this.current = this.current.charAt(0) === '-' ? this.current.slice(1) : `-${this.current}`;
    },
    percent() {
      this.current = `${parseFloat(this.current)/100}`;
    },
    append(number) {
      if (this.operatorClicked) {
          this.current = '';
          this.operatorClicked = false;
      }
      this.current = `${this.current}${number}`;
    },
    dot() {
      if(this.current.indexOf('.') === -1) {
        this.append('.');
      }
    },
    setPrevious() {
      this.previous = this.current;
      this.operatorClicked = true;
    },
    divide() {
      this.operator = (a,b) => a/b;
      this.setPrevious();
    },
    multiply() {
      this.operator = (a,b) => a*b;
      this.setPrevious();
    },
    add() {
      this.operator = (a,b) => a+b;
      this.setPrevious();
    },
    subtract() {
      this.operator = (a,b) => a-b;
      this.setPrevious();
    },
    equal(){
      this.current = `${this.operator(parseFloat(this.current), parseFloat(this.previous))}`;
      this.previous = null;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url("https://fonts.googleapis.com/css?family=Muli:400,700&display=swap");
.calculator {
  margin: auto;
  width: 30vw;
  font-size: 1.8vw;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}
.title{
   font-family: 'Muli', sans-serif;
   grid-column: 1/5;
   text-align: center;
   font-size: 2vw;
   font-weight: bold;
   margin-bottom: 5vh; 
}
.display {
  font-size: 3vw;
  max-width: 100%;
  height: 10vh;
  padding-top: 2vh;
  grid-column: 1/5;
  background-color: #333;
  color: white;
  opacity: 0.9;
}
.zero {
  grid-column: 1/3;
}
.btn {
  background-color: #f2f2f2;
  border: 1px solid #888;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
}
.operator {
  background-color: orange;
  color: white;
}
</style>
