<template>
  <div class="black-bg" v-if="modal.showYN">
    <div class="white-bg">
      <img :src="products[this.modal.index].image" alt="room" />
      <span>상품 번호 : {{ products[this.modal.index].id }} / 허위 매물 신고 수 : {{ products[this.modal.index].count }}건</span>
      <h4>{{ products[this.modal.index].title }}</h4>
      <p>{{ products[this.modal.index].content }}</p>
      <p>{{ products[this.modal.index].price }}원</p>
      <button @click="modalClose">모달창 닫기</button>
    </div>
  </div>
</template>

<script>
import { productsData } from "@/constants/products";

export default {
  name: "ProductModal",
  props: {
    modal: {
      type: {
        showYN: Boolean,
        index: String,
      },
      default: {
        showYN: false,
        index: 0,
      },
    },
  },
  data() {
    return {
      products: productsData,
    };
  },
  methods: {
    modalClose() {
      this.$emit("modal", false);
    },
  },
};
</script>

<style>
body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

img {
  width: 100%;
}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>
