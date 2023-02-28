<template>
  <div class="calculator">
    <div class="calculator-buttons">
     <div class="display">
      <p class="prev" v-if="prev!=''">{{ prev }} <br> = {{result}}</p>
      <div class="calc">
        {{calc || 0}}
      </div>
     </div>
     <p @click="clear">AC</p>
     <p @click="del">DEL</p>
     <p @click="hundredPercent">%</p>
     <p @click="addToCalc('/')">/</p>
     <p @click="addToCalc('7')">7</p>
     <p @click="addToCalc('8')">8</p>
     <p @click="addToCalc('9')">9</p>
     <p @click="addToCalc('*')">X</p>
     <p @click="addToCalc('4')">4</p>
     <p @click="addToCalc('5')">5</p>
     <p @click="addToCalc('6')">6</p>
     <p @click="addToCalc('-')">-</p>
     <p @click="addToCalc('1')">1</p>
     <p @click="addToCalc('2')">2</p>
     <p @click="addToCalc('3')">3</p>
     <p @click="addToCalc('+')">+</p>
     <p @click="addToCalc('00')">00</p>
     <p @click="addToCalc('0')">0</p>
     <p @click="point()">.</p>
     <p @click="calculate">=</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Calculator-app",
  data(){
  return{
    calc: '0',
    result:'',
    prev:'',
  }
 },
 methods:{
  clear(){
    this.calc='';
    this.result='';
    this.prev = '';
  },
  del(){
    this.calc=this.calc.slice(0,-1);
  },
  hundredPercent(){
    this.calc = `${parseFloat(this.calc / 100)}`
  },
  point(){
    let pointt = '.';
    this.calc= this.calc.indexOf(pointt)==-1? this.calc+pointt:this.calc
  },
  addToCalc(numOrOp){
    if(this.calc=='0'){
      this.calc='';
    }
    this.calc = this.calc + numOrOp;
  },
  calculate(){
    this.prev= this.calc
    console.log(this.prev)
    this.result = `${eval(this.calc)}`
    this.calc=this.result
  }
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style >
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body{
  background-color: #1E293B;
}
.calculator{
  background-color: #0F172A;
  width: fit-content;
  padding: 20px;
  margin: 0 auto;
  border-radius: 10px;
  border: 1px solid #335BDC;
}
.calculator-buttons{
  display: grid;
  justify-content: center;
  align-items: center;
  grid-template-columns: repeat(4,1fr);
  column-gap: 15px;
  row-gap: 15px;
}
.calculator-buttons .display{
  grid-column: 1 / 5;
  color: #fff;
  font-size: 2.3rem;
  font-weight: 900;
  background-color: #334155;
  height: 200px;
  border-radius: 5px;
  position: relative;
}
.calculator-buttons .display .calc{
  position: absolute;
  bottom: 0;
  right: 10px;
}
.calculator-buttons p{
  width:87px;
  height: 65px;
  background-color: #334155;
  border-radius: 5px;
  color: rgb(244, 225, 200);
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 2rem;
  font-weight: 700;
}
.calculator-buttons .display .prev{
  font-size: 0.9rem;
  color: red;
}
</style>
