<template>
  <div>
    <h1>원룸샵</h1>
    <div class="room" :key="i" v-for="(product, i) in products">
      <img :src="product.image" alt="room" />
      <h4>{{ product.name }}</h4>
      <p>{{ product.price }} 만원</p>
      <button @click="changeCounter(i)">허위 매물 신고</button>&nbsp;
      <span>신고 수 : {{ product.count }}</span>
      <br />
      <br />
      <button @click="modalHandler(i)">모달창 열기</button>
    </div>
  </div>
</template>

<script>
import { productsData } from "@/constants/products";

export default {
  name: "Products",
  data() {
    return {
      products: productsData,
    };
  },
  methods: {
    changeCounter(i) {
      this.products[i].count++;
    },
    modalHandler(index) {
      this.$emit("setIndex", index);
      this.$emit("modalShowHandler", true);
    },
  },
};
</script>

<style>
.room img {
  width: 500px;
  margin-top: 40px;
}
</style>
