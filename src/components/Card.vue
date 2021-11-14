<template>
  <div class="card-container">
    <div class="left">
      <div class="bill">
        <div>Bill</div>
        <input type="text" />
      </div>
      <div class="select-tip">
        <div>Select Tip %</div>
        <div class="tip-grid-container">
          <div>5%</div>
          <div>10%</div>
          <div>15%</div>
          <div>25%</div>
          <div>50%</div>
          <div>Custom</div>
        </div>
      </div>
      <div class="total-people">
        <div class="input-label">
          <div>Number of People</div>
          <div class="error">Can't be zero</div>
        </div>
        <input type="text" />
      </div>
    </div>
    <div class="right">
      <div class="right-inner">
        <div class="right-top">
          <div class="right-top-row">
            <div class="label">
              <div class="label-heading">Tip Amount</div>
              <div class="label-subheading">/ person</div>
            </div>
            <div class="price">$ 0.00</div>
          </div>
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
export default {
  name: 'Card',
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

input {
  width: 100%;
  line-height: 1.8;
  text-align: right;
  font-family: 'Space Mono', monospace;
  font-weight: 700;
  font-size: 16px;
}

.tip-grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
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
}

.reset-btn:hover {
  background-color: hsl(172, 67%, 65%);
}
</style>
