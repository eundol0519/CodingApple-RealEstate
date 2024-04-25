<template>
  <button @click="sortHandler('cheap-price')">가격 높은 순으로 정렬</button>
  &nbsp;
  <button @click="sortHandler('expensive-price')">가격 낮은 순으로 정렬</button>
  &nbsp;
  <button @click="sortHandler('title')">제목 순으로 정렬</button>
  &nbsp;
  <button @click="sortHandler">되돌리기</button>
  <div>
    <h1>원룸샵</h1>
    <div class="room" :key="i" v-for="(product, i) in products">
      <img :src="product.image" alt="room" />
      <h4>{{ product.title }}</h4>
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
    sortHandler(sortType) {
      switch (sortType) {
        case "title": // 문자열 정렬
          this.products = [...this.products].sort((a, b) => (a.title < b.title ? -1 : a.title > b.title ? 1 : 0));
          break;
        case "expensive-price": // 숫자 정렬
          this.products = [...this.products].sort((a, b) => a.price - b.price);
          break;
        case "cheap-price": // 숫자 정렬
          this.products = [...this.products].sort((a, b) => b.price - a.price);
          break;
        default:
          this.products = productsData;
          break;
      }
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
