<script>
export default {
  name: 'Calculate',
  data() {
    return {
      displayNumber: '',
      storedDisplayNumber: '',
      enteredOperator: ''
    }
  },
  methods: {
    creatingDisplayNumber(digit) {
      if (this.displayNumber == '0') {
        this.displayNumber = ''
      }
      this.displayNumber += digit
    },
    operatorCalc(operator) {

      this.storedDisplayNumber = this.displayNumber
      this.displayNumber = ''

      switch (operator) {
        case '/':
          this.enteredOperator = '/'
          break;

        case '*':
          this.enteredOperator = '*'
          break;

        case '+':
          this.enteredOperator = '+'
          break;

        case '-':
          this.enteredOperator = '-'
          break;

        case '%':
          this.enteredOperator = '%'
          break;

        case 'C':
          this.displayNumber = ''
          this.storedDisplayNumber = ''
          this.enteredOperator = ''
          break;

        default:
          break;
      }
    },
    calc() {
      switch (this.enteredOperator) {
        case '/':
          this.displayNumber = parseFloat(this.displayNumber)
          this.storedDisplayNumber = parseFloat(this.storedDisplayNumber)
          this.storedDisplayNumber /= this.displayNumber
          this.displayNumber = this.storedDisplayNumber
          break;

        case '*':
          this.displayNumber = parseFloat(this.displayNumber)
          this.storedDisplayNumber = parseFloat(this.storedDisplayNumber)
          this.storedDisplayNumber *= this.displayNumber
          this.displayNumber = this.storedDisplayNumber
          break;

        case '+':
          this.displayNumber = parseFloat(this.displayNumber)
          this.storedDisplayNumber = parseFloat(this.storedDisplayNumber)
          this.storedDisplayNumber += this.displayNumber
          this.displayNumber = this.storedDisplayNumber
          break;

        case '-':
          this.displayNumber = parseFloat(this.displayNumber)
          this.storedDisplayNumber = parseFloat(this.storedDisplayNumber)
          this.storedDisplayNumber -= this.displayNumber
          this.displayNumber = this.storedDisplayNumber
          break;

        case '%':
          this.displayNumber = parseFloat(this.displayNumber)
          this.storedDisplayNumber = parseFloat(this.storedDisplayNumber)
          this.storedDisplayNumber %= this.displayNumber
          this.displayNumber = this.storedDisplayNumber
          break;

        default:
          break;
      }
    },
    dot(dot) {
      if (!this.displayNumber.includes('.')) {
        this.displayNumber += dot
      }
    }
  }
}
</script>

<template>

  <section class="container">

    <div class="calc-container">

      <div class="calc-digit-container">
        <span class="zero-top">
          {{ displayNumber ? displayNumber : '0' }}
        </span>
      </div>

      <div class="calc-digit-container">
        <span @click="operatorCalc('/')" class="operators">
          /
        </span>
        <span @click="operatorCalc('%')" class="digits-operators">
          %
        </span>
        <span class="digits-operators">
          +/-
        </span>
        <span @click="operatorCalc('C')" class="digits-operators">
          C
        </span>
      </div>

      <div class="calc-digit-container">
        <span @click="operatorCalc('*')" class="operators">
          *
        </span>
        <span @click="creatingDisplayNumber('9')" class="digits-operators">
          9
        </span>
        <span @click="creatingDisplayNumber('8')" class="digits-operators">
          8
        </span>
        <span @click="creatingDisplayNumber('7')" class="digits-operators">
          7
        </span>
      </div>

      <div class="calc-digit-container">
        <span @click="operatorCalc('-')" class="operators">
          -
        </span>
        <span @click="creatingDisplayNumber('6')" class="digits-operators">
          6
        </span>
        <span @click="creatingDisplayNumber('5')" class="digits-operators">
          5
        </span>
        <span @click="creatingDisplayNumber('4')" class="digits-operators">
          4
        </span>
      </div>

      <div class="calc-digit-container">
        <span @click="operatorCalc('+')" class="operators">
          +
        </span>
        <span @click="creatingDisplayNumber('3')" class="digits-operators">
          3
        </span>
        <span @click="creatingDisplayNumber('2')" class="digits-operators">
          2
        </span>
        <span @click="creatingDisplayNumber('1')" class="digits-operators">
          1
        </span>
      </div>

      <div class="calc-digit-container">
        <span @click="calc" class="operators">
          =
        </span>
        <span @click="dot('.')" class="digits-operators">
          .
        </span>
        <span @click="creatingDisplayNumber('0')" class="zero-bottom">
          0
        </span>
      </div>

    </div>

  </section>

</template>

<style scoped>
.container {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  margin: 10rem auto;
  width: 100%;
}

.calc-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 30vw;
}

.calc-digit-container {
  display: flex;
  flex-direction: row-reverse;
  align-items: center;
  justify-content: center;
  width: 100%;
}

.zero-top {
  width: 100%;
  text-align: center;
  color: white;
  font-size: 40px;
  font-weight: 700;
  background-color: rgb(49, 48, 48);
}

.operators {
  width: 25%;
  text-align: center;
  color: white;
  font-size: 30px;
  font-weight: 700;
  background-color: rgb(158, 167, 26);
  border: 1px solid gray;
  cursor: pointer;
}

.digits-operators {
  width: 25%;
  text-align: center;
  color: rgb(49, 48, 48);
  font-size: 30px;
  font-weight: 700;
  background-color: white;
  border: 1px solid gray;
  cursor: pointer;
}

.zero-bottom {
  width: 50%;
  text-align: center;
  color: rgb(49, 48, 48);
  font-size: 30px;
  font-weight: 700;
  background-color: white;
  border: 1px solid gray;
  cursor: pointer;
}
</style>