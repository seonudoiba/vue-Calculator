<template>
<section class="bg-light mx-auto my-5 mainsec ">
  <div class="AnswerDisplay my-3">
    <div class="display  px-2 curentValue" :class= " {scroll: ShowValue.length > 15}">{{ShowValue}}</div>
    <div class="display  px-2 calcValue">{{calcValue}}</div>
  </div>
  <div class= "numbuttons ">
    <button @click="pressed('x2')" class="btn border btn-primary m-1 " type="button">x<sup>2</sup></button>
    <button @click="pressed('log(')" class="btn border btn-primary m-1 " type="button">log</button>
    <button @click="pressed('sin(')" class="btn border btn-primary m-1 " type="button">sin</button>
    <button @click="pressed('cos(')" class="btn border btn-primary m-1 " type="button">cos</button>
    <button @click="pressed('tan(')" class="btn border btn-primary m-1 " type="button">tan</button>
    <button @click="pressed('1/')" class="btn border btn-primary m-1 " type="button">x<sup>-1</sup></button>
    <button @click="pressed('√')" class="btn border btn-primary m-1 " type="button">√</button>
    <button @click="pressed('3√')" class="btn border btn-primary m-1 " type="button"><sup>3</sup>√</button>
    <button @click="pressed('(-)')" class="btn border btn-primary m-1 " type="button">(-)</button>
    <button @click="pressed('DEL')" class="btn border btn-primary m-1 " type="button">DEL</button>
    <button @click="pressed('C')" class="btn border btn-primary m-1 " type="button">C</button>
    <button @click="pressed('x')" class="btn border btn-primary m-1 " type="button">X</button>
    <button @click="pressed('7')" class="btn border btn-primary m-1 " type="button">7</button>
    <button @click="pressed('8')" class="btn border btn-primary m-1 " type="button">8</button>
    <button @click="pressed('9')" class="btn border btn-primary m-1 " type="button">9</button>
    <button @click="pressed('/')" class="btn border btn-primary m-1 " type="button">÷</button>
    <button @click="pressed('4')" class="btn border btn-primary m-1 " type="button">4</button>
    <button @click="pressed('5')" class="btn border btn-primary m-1 " type="button">5</button>
    <button @click="pressed('6')" class="btn border btn-primary m-1 " type="button">6</button>
    <button @click="pressed('-')" class="btn border btn-primary m-1 " type="button">-</button>
    <button @click="pressed('1')" class="btn border btn-primary m-1 " type="button">1</button>
    <button @click="pressed('2')" class="btn border btn-primary m-1 " type="button">2</button>
    <button @click="pressed('3')" class="btn border btn-primary m-1 " type="button">3</button>
     <button @click="pressed('+')" class="btn border btn-primary m-1 " type="button">+</button>
    <button @click="pressed('0')" class="btn border btn-primary m-1 " type="button">0</button>
    <button @click="pressed('.')" class="btn border btn-primary m-1 " type="button">.</button>
    <button @click="pressed('%')" class="btn border btn-primary m-1 " type="button">%</button>
    <button @click="pressed('=')" class="btn border btn-primary m-1 " type="button">=</button>
   
  </div>
</section>
  
</template>

<script>

export default {
  
  name: 'App',
  components: {
    // HelloWorld
  },
  data() {
    return {
      calcValue : "",
      currentValue : "",
      previousValue: "",
      numbers :['0','1','2','3','4','5','6','7','8','9','.',],
      signs :['+','x','/','-',"%",],
      maths :['log(','sin(','cos(','tan(','√','3√' ],
      sign: "",
      ShowValue: "",
    }
  },
  methods: {
    pressed(value){
      if(this.numbers.includes(value)){
        this.currentValue = this.currentValue + value;
        this.ShowValue = this.ShowValue + value;

      }
      else if (this.signs.includes(value)){
        this.previousValue = this.currentValue;
        this.ShowValue = this.ShowValue + value;
        this.sign = value
        this.currentValue=""
        // this.calcValue
       
        
      }
      else if (this.maths.includes(value)){
        this.previousValue = '';
        this.currentValue ='',
        this.ShowValue =  value;
        this.sign = value
        // this.calcValue
       
        
      }
      else if (value == 'x2'){
      
        this.ShowValue = this.ShowValue + '^2';
        this.sign = value;
        // this.calcValue
       
        
      }
      else if (value == '1/'){
      
        this.ShowValue = this.ShowValue + '^-1';
        this.sign = value;
        // this.calcValue
       
        
      }
      else if (value == '='){
        
            if(this.sign == '+'){
                this.calcValue = Number(this.previousValue) + Number(this.currentValue);
                this.currentValue = this.calcValue;
                this.ShowValue = this.calcValue;
            }else if (this.sign == '-'){
              this.calcValue = Number(this.previousValue) - Number(this.currentValue);
              this.currentValue = this.calcValue;
              this.ShowValue = this.calcValue;
            }
          else if (this.sign == '/'){
              this.calcValue = Number(this.previousValue) / Number(this.currentValue);
              this.currentValue = this.calcValue;
              this.ShowValue = this.calcValue;
          } else if (this.sign == '1/'){
              this.calcValue = 1 / Number(this.currentValue);
              this.currentValue = this.calcValue;
              this.ShowValue = this.calcValue;
          }
          else if (this.sign == 'x'){
              this.calcValue = Number(this.previousValue) * Number(this.currentValue);
              this.currentValue = this.calcValue;
              this.ShowValue = this.calcValue;
          }
          else if (this.sign == '%'){
              this.calcValue = Number(this.previousValue) % Number(this.currentValue);
              this.currentValue = this.calcValue;
              this.ShowValue = this.calcValue;
          }else if(this.sign =='x2'){
            this.calcValue = Math.pow(this.currentValue, 2);
            this.currentValue = this.calcValue;
            this.ShowValue = this.calcValue;
            // this.showValue = this.calcValue
          } else if(this.sign =='log('){
            this.calcValue = Math.log10(this.currentValue);
            this.currentValue = this.calcValue;
            this.ShowValue = this.calcValue;
          }else if(this.sign =='sin('){
            this.calcValue = Math.sin(this.currentValue * (Math.PI/180));
            this.currentValue = this.calcValue;
            this.ShowValue = this.calcValue;
          }
          else if(this.sign =='cos('){
            this.calcValue = Math.cos(this.currentValue * (Math.PI/180));
            this.currentValue = this.calcValue;
            this.ShowValue = this.calcValue;
          }
          else if(this.sign =='tan('){
            this.calcValue = Math.tan(this.currentValue * (Math.PI/180));
            this.currentValue = this.calcValue;
            this.ShowValue = this.calcValue;
          }
          else if(this.sign =='√'){
            this.calcValue = Math.sqrt(this.currentValue);
            this.currentValue = this.calcValue;
            this.ShowValue = this.calcValue;
          }
          else if(this.sign =='3√'){
            this.calcValue =  Math.cbrt(this.currentValue);
            this.currentValue = this.calcValue;
            this.ShowValue = this.calcValue;
          }
      } else if(value =='C'){
        this.calcValue = '0'
        this.previousValue = ""
        this.currentValue = ""
        this.ShowValue = '';
      }
      else if(value =='DEL'){
        this.previousValue = this.previousValue.slice(0,-1)
        this.currentValue = this.currentValue.slice(0,-1)
        this.ShowValue = this.ShowValue.slice(0,-1)
      }
      else if(value =='(-)'){
        this.currentValue = this.currentValue + '-';
        this.ShowValue = this.ShowValue + '-';
      }
      
     
      
    }
  }
}
</script>

<style>
.mainsec {
  height:470px;
  border-radius: 20px;
  width:27%;
  background-color:green;
  padding-top: 15px;
  border: 1px solid  rgb(42, 42, 255)
}
.answerDisplay{
  border-radius: 20px;
}
.numbuttons{
  display:grid;
  grid-template-columns: auto auto auto auto;
}
.display {
  width: 100%;
  height:40px;
  font-size: 1.7rem;
  /* border: 1px solid gray; */
}
.calcValue{
  text-align: right;
}
.scroll{
  overflow-x: hidden;
}
@media only screen and (max-width: 600px) {
  .mainsec {
    height:100%;
    width:90%;
}
}

</style>
