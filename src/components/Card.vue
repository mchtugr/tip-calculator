<template>
  <div class="card-container">
    <!-- Left Screen -->
    <div class="left">
      <!-- Total Bill -->
      <div class="bill">
        <div class="input-label">Bill</div>
        <div class="input-icon">
          <dollar-svg />
        </div>
        <input type="number" placeholder="0" v-model="totalBill" />
      </div>
      <!-- Tip Percent -->
      <div class="select-tip">
        <div class="input-label">Select Tip %</div>
        <div class="tip-grid-container">
          <input
            id="five"
            value="5"
            type="radio"
            name="percent"
            v-model="tipPercent"
            @click="removeCustomInput"
          />
          <label for="five" class="tip-percent">5% </label>
          <input
            id="ten"
            value="10"
            name="percent"
            type="radio"
            v-model="tipPercent"
            @click="removeCustomInput"
          />
          <label for="ten" class="tip-percent">10% </label>
          <input
            id="fifteen"
            value="15"
            type="radio"
            name="percent"
            v-model="tipPercent"
            @click="removeCustomInput"
          />
          <label for="fifteen" class="tip-percent">15% </label>
          <input
            id="twentyfive"
            value="25"
            type="radio"
            name="percent"
            v-model="tipPercent"
            @click="removeCustomInput"
          /><label for="twentyfive" class="tip-percent">25% </label>
          <input
            id="fifty"
            value="50"
            type="radio"
            name="percent"
            v-model="tipPercent"
            @click="removeCustomInput"
          />
          <label for="fifty" class="tip-percent">50% </label>
          <label @click="handleCustomRadio">
            <input
              id="custom"
              value="custom"
              type="radio"
              name="percent"
              v-model="tipPercent"
            />
            <input
              class="tip-percent custom"
              v-model="customTip"
              type="number"
              placeholder="Custom"
            />
          </label>
        </div>
      </div>
      <!-- Total People -->
      <div class="total-people">
        <div class="input-label">
          <div>Number of People</div>
          <!-- show error when input is emty or smaller than 1 -->
          <div class="error" v-if="!totalPeople || totalPeople < 1">
            Can't be zero
          </div>
        </div>
        <div class="input-icon">
          <person-svg />
        </div>
        <input type="number" placeholder="0" v-model="totalPeople" />
      </div>
    </div>
    <!-- Right Screen -->
    <div class="right">
      <div class="right-inner">
        <div class="right-top">
          <!-- Tip per person -->
          <div class="right-top-row">
            <div class="label">
              <div class="label-heading">Tip Amount</div>
              <div class="label-subheading">/ person</div>
            </div>
            <div class="price">
              $ {{ displayResult ? tipPerPerson : '0.00' }}
            </div>
          </div>
          <!-- Total per person -->
          <div class="right-top-row">
            <div class="label">
              <div class="label-heading">Total</div>
              <div class="label-subheading">/ person</div>
            </div>
            <div class="price">
              $ {{ displayResult ? totalPerPerson : '0.00' }}
            </div>
          </div>
        </div>
        <div class="right-bottom">
          <button class="reset-btn" @click="resetForm">Reset</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import DollarSvg from './ui/DollarSvg.vue'
import PersonSvg from './ui/PersonSvg.vue'
export default {
  name: 'Card',
  components: {
    DollarSvg,
    PersonSvg,
  },
  data() {
    return {
      customTip: null,
      tipPercent: null,
      totalPeople: null,
      totalBill: null,
    }
  },
  methods: {
    handleCustomRadio() {
      document.getElementById('custom').checked = true
      this.tipPercent = 'custom'
    },
    removeCustomInput() {
      this.custom = null
    },
    // clear all states and results
    resetForm() {
      this.tipPercent = null
      this.totalPeople = null
      this.totalBill = null
      this.customTip = null
    },
  },
  computed: {
    // convert str to number, if custom radio selected return custom input value
    numberTipPercent() {
      if (this.tipPercent === 'custom') {
        return Number(this.customTip) / 100
      } else {
        return Number(this.tipPercent) / 100
      }
    },
    // convert to Num
    numberTotalBill() {
      return Number(this.totalBill)
    },
    // convert to Num
    numberTotalPeople() {
      return Number(this.totalPeople)
    },
    displayResult() {
      // if one of the input is not available, do not calculate tip
      if (
        !this.numberTotalPeople ||
        !this.numberTipPercent ||
        !this.numberTotalBill
      ) {
        return false
      } else {
        return true
      }
    },
    tipPerPerson() {
      return (
        (this.numberTotalBill * this.numberTipPercent) /
        this.numberTotalPeople
      ).toFixed(2)
    },
    totalPerPerson() {
      return (
        this.numberTotalBill / this.numberTotalPeople +
        Number(this.tipPerPerson)
      ).toFixed(2)
    },
  },
}
</script>

<style>
.card-container {
  background-color: #fff;
  max-width: 700px;
  margin: 0;
  padding: 20px;
  border-radius: 15px;
  display: flex;
}

.left {
  width: 50%;
  padding: 20px;
  display: grid;
  grid-template-rows: 1fr 2fr 1fr;
}
.input-label {
  display: flex;
  justify-content: space-between;
  margin: 5px 0;
}

input[type='radio']:checked {
  display: none;
}

input[type='radio'] {
  display: none;
}

input {
  width: 100%;
  line-height: 2.4;
  text-align: right;
  font-family: 'Space Mono', monospace;
  font-weight: 700;
  font-size: 16px;
  background-color: hsl(185, 41%, 84%);
  border: none;
  border-radius: 3px;
  box-sizing: border-box;
  padding: 0 10px;
}

input[type='radio']:checked + label {
  background-color: hsl(172, 67%, 45%);
}

.tip-grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 8px;
}

.right {
  width: 50%;
  padding: 20px;
}

.right-inner {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  background-color: hsl(183, 100%, 15%);
  border-radius: 15px;
  padding: 30px;
  color: #fff;
  box-sizing: border-box;
}

.right-top-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}

.label-heading {
  font-size: 14px;
}

.label-subheading {
  font-size: 11px;
  color: hsl(185, 41%, 84%);
}

.price {
  font-size: 30px;
  font-weight: 700;
  color: hsl(172, 67%, 45%);
}

.reset-btn {
  width: 100%;
  padding: 10px;
  border-radius: 5px;
  border: none;
  text-transform: uppercase;
  font-weight: 700;
  background-color: hsl(172, 67%, 45%);
  color: hsl(183, 100%, 15%);
}

.reset-btn:hover {
  background-color: hsl(172, 67%, 65%);
}

.bill {
  position: relative;
}

.total-people {
  position: relative;
}

.input-icon {
  position: absolute;
  bottom: 6px;
  left: 10px;
}

.tip-percent {
  background-color: hsl(183, 100%, 15%);
  text-align: center;
  line-height: 2.4;
  color: hsl(0, 0%, 100%);
  border-radius: 5px;
}

.custom {
  background-color: hsl(185, 41%, 84%);
  color: black;
}

/* Chrome, Safari, Edge, Opera */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

/* Firefox */
input[type='number'] {
  -moz-appearance: textfield;
}

.error {
  color: red;
}

@media (max-width: 768px) {
  .card-container {
    width: 90%;
    display: block;
  }
  .left {
    width: 90%;
  }

  .right {
    width: 90%;
  }
}

@media (max-width: 576px) {
  .tip-grid-container {
    grid-template-columns: 1fr 1fr;
  }

  .input-icon {
    bottom: 16px;
  }
}
</style>
