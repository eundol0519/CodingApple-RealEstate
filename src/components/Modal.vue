<template>
  <div class="black-bg" v-if="modal.showYN">
    <div class="white-bg">
      <span>상품 번호 : {{ product.id }}</span>
      <h4>{{ product.title }}</h4>
      <p>{{ product.content }}</p>
      <p>{{ product.price }}</p>
      <button @click="modalClose">모달창 닫기</button>
    </div>
  </div>
</template>

<script>
import { productsData } from "@/constants/products";

export default {
  name: "ModalComponent",
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
      product: productsData[this.modal.index],
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
