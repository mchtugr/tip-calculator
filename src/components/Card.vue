<template>
  <div class="card-container">
    <!-- Left Screen -->
    <div class="left">
      <!-- Total Bill -->
      <div class="bill">
        <div>Bill</div>
        <div class="dollar-svg">
          <dollar-svg />
        </div>
        <input type="number" placeholder="0" />
      </div>
      <!-- Tip Percent -->
      <div class="select-tip">
        <div>Select Tip %</div>
        <div class="tip-grid-container">
          <input
            id="five"
            value="five"
            type="radio"
            name="percent"
            v-model="tipPercent"
          />
          <label for="five" class="tip-percent">5% </label>
          <input
            id="ten"
            value="ten"
            name="percent"
            type="radio"
            v-model="tipPercent"
          />
          <label for="ten" class="tip-percent">10% </label>
          <input
            id="fifteen"
            value="fifteen"
            type="radio"
            name="percent"
            v-model="tipPercent"
          />
          <label for="fifteen" class="tip-percent">15% </label>
          <input
            id="twentyfive"
            value="twentyfive"
            type="radio"
            name="percent"
            v-model="tipPercent"
          /><label for="twentyfive" class="tip-percent">25% </label>
          <input
            id="fifty"
            value="fifty"
            type="radio"
            name="percent"
            v-model="tipPercent"
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
              v-model="custom"
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
          <div class="error">Can't be zero</div>
        </div>
        <div class="dollar-svg">
          <person-svg />
        </div>
        <input type="number" placeholder="0" />
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
            <div class="price">$ 0.00</div>
          </div>
          <!-- Total per person -->
          <div class="right-top-row">
            <div class="label">
              <div class="label-heading">Total</div>
              <div class="label-subheading">/ person</div>
            </div>
            <div class="price">$ 0.00</div>
          </div>
        </div>
        <div class="right-bottom">
          <button class="reset-btn">Reset</button>
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
    return {}
  },
  methods: {
    handleCustomRadio() {
      document.getElementById('custom').checked = <true></true>
    },
  },
}
</script>

<style>
.card-container {
  background-color: #fff;
  min-height: 350px;
  width: 700px;
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
  /* padding: 20px; */
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

.dollar-svg {
  position: absolute;
  bottom: 20px;
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
</style>
