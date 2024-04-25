<template>
  <!-- <Transition name="fade">
    <ProductModal :modal="modal" @modalShowHandler="modalShowHandler" />
  </Transition> -->
  <div class="start" :class="{ end: modal.showYN }">
    <!-- :class="{ end : modal.showYN }" : class에 데이터 바인딩 할 때 Object({}) 형식을 사용하면 value의 값이 true일 때 key에 있는 class가 노출된다. -->
    <ProductModal :modal="modal" @modalShowHandler="modalShowHandler" />
  </div>
  <Navbar />
  <Discount v-if="showDiscount" />
  <Products @setIndex="setIndex" @modalShowHandler="modalShowHandler" />
</template>

<script>
import Navbar from "./components/common/Navbar.vue";
import ProductModal from "./components/products/ProductModal.vue";
import Products from "./components/products/Products.vue";
import Discount from "./components/main/Discount.vue";

export default {
  name: "App",
  components: {
    ProductModal,
    Navbar,
    Products,
    Discount,
  },
  data() {
    return {
      modal: {
        showYN: false,
        index: 0,
      },
      showDiscount: true,
    };
  },
  methods: {
    setIndex(index) {
      this.modal.index = index;
    },
    modalShowHandler(state) {
      this.modal.showYN = state;
    },
  },
  mounted() {
    // - 2초 후 showDiscount를 false로 변경해주는 코드
    // setTimeout(() => {
    //   this.showDiscount = false;
    // }, 2000);
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}

.start {
  opacity: 0;
  transition: all 1s;
}

.end {
  opacity: 1;
  transition: all 1s;
}

.fade-enter-from {
  opacity: 0;
}

.fade-enter-active {
  transition: all 1s;
}

.fade-enter-to {
  opacity: 1;
}

.fade-leave-from {
  opacity: 1;
}

.fade-leave-active {
  transition: all 1s;
}

.fade-leave-to {
  opacity: 0;
}
</style>
