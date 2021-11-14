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
          <div class="tip-amount">
            <div class="label">
              <div>Tip Amount</div>
              <div>/ person</div>
            </div>
            <div class="price">$ 0.00</div>
          </div>
          <div class="total">
            <div class="label">
              <div>Tip Amount</div>
              <div>/ person</div>
            </div>
            <div class="price">$ 0.00</div>
          </div>
        </div>
        <div class="right-bottom">
          <button>Reset</button>
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
  height: 300px;
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
}

.tip-grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
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
}
</style>
