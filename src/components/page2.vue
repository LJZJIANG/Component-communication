<template>
    <div>
        <p>
            <span>总金额：{{totalMoney}}元 </span>剩余金额：
            <span>{{balance}}元</span>
        </p>
    </div>
</template>
<script>
import bus from "../eventBus.js";
export default {
  data() {
    return {
      balance: 1000,
      totalMoney: 1000
    };
  },
  mounted() {
    bus.$on("priceChange", (price, count) => {
      this.balance = this.totalMoney - price * count;
    });
    console.log(this.$parent)
  }
};
</script>
