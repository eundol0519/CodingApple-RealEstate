<template>
  <div class="black-bg" v-if="modal.showYN">
    <div class="white-bg">
      <img :src="products[this.modal.index].image" alt="room" />
      <br />
      <span>상품 번호 : {{ products[this.modal.index].id }} / 허위 매물 신고 수 : {{ products[this.modal.index].count }}건</span>
      <h4>{{ products[this.modal.index].title }}</h4>
      <p>{{ products[this.modal.index].content }}</p>
      <!-- <input v-on:input="months = $event.target.value" :value="months" placeholder="개월 수를 입력해주세요" /> -->
      <input v-model="months" placeholder="개월 수를 입력해주세요" />
      <p>{{ this.months || 0 }} * {{ products[this.modal.index].price }} = {{ this.months * products[this.modal.index].price }}원</p>
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
      months: 1,
    };
  },
  methods: {
    modalClose() {
      this.$emit("modalShowHandler", false);
    },
  },
  // watch: {
  //   months(value) {
  //     if (isNaN(value)) {
  //       alert("숫자만 입력해주세요.");
  //       this.months = 1;
  //       return;
  //     }
  //   },
  // },
  updated() {
    if (Number(this.months) === 2) {
      alert("2개월입니다.");
    }
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
  width: 500px;
}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.white-bg {
  width: fit-content;
  height: fit-content;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>
