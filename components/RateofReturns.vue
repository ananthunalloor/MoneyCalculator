<template>
  <div>
    <br />
    <h3>RATE OF RETURN</h3>
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
        v-model="finalbalance"
        type="number"
        name="Desired Balance"
        label="Desired Balance"
        placeholder="200,000"
        :rules="[{ required: true, message: 'Desired Balance is required' }]"
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
          Your Rate of Returns is <b>{{ rateofreturns }}</b>
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
      rateofreturns: '0',
      terms: '',
      finalbalance: '',
      interestearned: '0',
    }
  },
  methods: {
    onSubmit(values) {
      console.log('submit', values)
      this.rateofreturns = ((12 * ( Math.pow((this.finalbalance / this.intialinvestment),( 1 / (12 * this.terms))) - 1)) * 100).toFixed(3);
      this.interestearned = (this.finalbalance - this.intialinvestment).toFixed(
        3
      );
      console.log(this.finalbalance)
    },
  },
}
</script>
