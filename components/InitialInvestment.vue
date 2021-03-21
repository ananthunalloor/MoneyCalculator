<template>
  <div>
    <br />
    <h3>INTIAL INVESTMENT</h3>
    <br />

    <van-form @submit="onSubmit">
      <van-field
        v-model="finalbalance"
        type="number"
        name="Desired Balance"
        label="Desired Balance"
        placeholder="200,000"
        :rules="[{ required: true, message: 'Desired Balance is required' }]"
      />
      <van-field
        v-model="rateofreturns"
        type="number"
        name="Rate of Returns"
        label="Rate of Returns"
        placeholder="5%"
        :rules="[{ required: true, message: 'Rate of Returns' }]"
      />
      <van-field
        v-model="terms"
        type="number"
        name="Terms"
        label="Terms"
        placeholder="10 Years"
        :rules="[{ required: true, message: 'Terms is required' }]"
      />
      <div>
        <br />
        <p>
          Your initial deposit needs to be <b>{{ intialinvestment }}</b>
        </p>
        <br />
        <p>
          You earn <b>{{ interestearned }}</b> on your investment.
        </p>
        <br />
      </div>
      <div style="margin: 16px">
        <van-button round block type="info" native-type="submit">
          Calculate
        </van-button>
      </div>
    </van-form>
  </div>
</template>
<script>
export default {
  data() {
    return {
      intialinvestment: '0',
      rateofreturns: '',
      terms: '',
      finalbalance: '',
      interestearned: '0',
    }
  },
  methods: {
    onSubmit(values) {
      console.log('submit', values)
      this.intialinvestment = (this.finalbalance/(Math.pow(1 + this.rateofreturns / 100 / 12, 12 * this.terms))).toFixed(3);
      this.interestearned = (this.finalbalance - this.intialinvestment).toFixed(
        3
      )
      console.log(this.finalbalance)
    },
  },
}
</script>
