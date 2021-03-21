<template>
  <div>
    <br />
    <h3>FINAL BALANCE</h3>
    <br />

    <van-form @submit="onSubmit">
      <van-field
        v-model="intialinvestment"
        type="number"
        name="Intial Investment"
        label="Intial Investment"
        placeholder="10000"
        :rules="[{ required: true, message: 'Intial Investment is required' }]"
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
          Your final balance will be <b>{{ finalbalance }}</b>
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
      intialinvestment: '',
      rateofreturns: '',
      terms: '',
      finalbalance: '0',
      interestearned: '0',
    }
  },
  methods: {
    onSubmit(values) {
      console.log('submit', values)
      this.finalbalance = (
        this.intialinvestment *
        Math.pow(1 + this.rateofreturns / 100 / 12, 12 * this.terms)
      ).toFixed(3)
      this.interestearned = (this.finalbalance - this.intialinvestment).toFixed(
        3
      )
      console.log(this.finalbalance)
    },
  },
}
</script>
