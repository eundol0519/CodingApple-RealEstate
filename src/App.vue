<template>
  <ProductModal :modal="modal" @modalShowHandler="modalShowHandler" />
  <Navbar />
  <div class="discount">
    <h4>지금 결제하면 20% 할인</h4>
  </div>
  <Products @setIndex="setIndex" @modalShowHandler="modalShowHandler" />
</template>

<script>
import Navbar from "./components/common/Navbar.vue";
import ProductModal from "./components/products/ProductModal.vue";
import Products from "./components/products/Products.vue";

export default {
  name: "App",
  components: {
    ProductModal,
    Navbar,
    Products,
  },
  data() {
    return {
      modal: {
        showYN: false,
        index: 0,
      },
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
</style>
