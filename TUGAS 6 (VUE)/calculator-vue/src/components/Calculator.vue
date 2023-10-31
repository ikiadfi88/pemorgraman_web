<template>
  <div class="calculator">
    <input type="text" v-model="expression" class="display" />
    <table>
      <tr>
        <td><button class="number" @click="operasi('7')">7</button></td>
        <td><button class="number" @click="operasi('8')">8</button></td>
        <td><button class="number" @click="operasi('9')">9</button></td>
        <td><button class="symbol" @click="operasi('+')">+</button></td>
      </tr>
      <tr>
        <td><button class="number" @click="operasi('4')">4</button></td>
        <td><button class="number" @click="operasi('5')">5</button></td>
        <td><button class="number" @click="operasi('6')">6</button></td>
        <td><button class="symbol" @click="operasi('-')">-</button></td>
      </tr>
      <tr>
        <td><button class="number" @click="operasi('1')">1</button></td>
        <td><button class="number" @click="operasi('2')">2</button></td>
        <td><button class="number" @click="operasi('3')">3</button></td>
        <td><button class="symbol" @click="operasi('*')">x</button></td>
      </tr>
      <tr>
        <td><button class="number" @click="operasi('0')">0</button></td>
        <td><button class="number" @click="hapus">C</button></td>
        <td><button class="symbol" @click="calculate">=</button></td>
        <td><button class="symbol" @click="operasi('/')">/</button></td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      expression: "",
    };
  },
  methods: {
    operasi(value) {
      this.expression += value;
    },
    hapus() {
      this.expression = "";
    },
    calculate() {
      try {
        this.expression = eval(this.expression).toString();
      } catch (error) {
        this.expression = "Error";
      }
    },
  },
};
</script>

<style scoped>
.calculator {
  display: flex;
  justify-content: center;
  align-items: center;
  border: 2px solid #ccc;
  border-radius: 10px;
  padding: 10px;
}

.display {
  width: 100%;
  text-align: right;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.number,
.symbol {
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 5px;
  cursor: pointer;
}

.number:hover,
.symbol:hover {
  background-color: #eee;
}

input {
  width: 100%;
  border: none;
  outline: none;
}

table {
  width: 100%;
  text-align: center;
  border-spacing: 10px;
}
</style>
