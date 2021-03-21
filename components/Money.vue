<template>
  <div>
    <h1>Investment Calculator</h1>
    <br>
    <div>
      <van-tabs v-model="activeName">
        <van-tab title="FINAL BALANCE" name="a">
            <final-balance/>
        </van-tab>
        <van-tab title="INTIAL INVESTMENT" name="b">
            <initial-investment/>
        </van-tab>
        <van-tab title="RATE OF RETURN" name="c">
            <rateof-returns/>
        </van-tab>
      </van-tabs>
    </div>
  </div>
</template>
<style scoped></style>
<script>
import FinalBalance from '~/components/FinalBalance.vue';
import InitialInvestment from '~/components/InitialInvestment.vue';
import RateofReturns from '~/components/RateofReturns.vue';
export default {
    components:{
        FinalBalance,
        InitialInvestment,
        RateofReturns,
    },
  data() {
    return {
      activeName: 'a',
    }
  }
}
</script>
