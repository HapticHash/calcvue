<template>
  <div class="calculator">
   <div class="display">{{current || '0'}}</div>
   <div @click="clear" class="btn">A/C</div>
   <div @click="sign" class="btn">+/-</div>
   <div @click="percent" class="btn">%</div>
   <div class="btn operator">÷</div>
   <div class="btn">7</div>
   <div class="btn">8</div>
   <div class="btn">9</div>
   <div class="btn operator">x</div>
   <div class="btn">4</div>
   <div class="btn">5</div>
   <div class="btn">6</div>
   <div class="btn operator">-</div>
   <div class="btn">1</div>
   <div class="btn">2</div>
   <div class="btn">3</div>
   <div class="btn operator">+</div>
   <div class="btn zero">0</div>
   <div class="btn">.</div>
   <div class="btn operator">=</div>

  </div>
</template>

<script>
export default {
  data() {
    return {
      current: '123',
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
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.calculator {
  margin: auto;
  width: 30vw;
  font-size: 1.5vw;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}
.display {
  font-size: 2.5vw;
  grid-column: 1/5;
  background-color: #333;
  color: white;
}
.zero {
  grid-column: 1/3;
}
.btn {
  background-color: #f2f2f2;
  border: 1px solid #888;
}
.operator {
  background-color: orange;
  color: white;
}
</style>
