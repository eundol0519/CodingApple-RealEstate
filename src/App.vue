<template>
  <Modal :modal="modal" @modal="modalShowHandler" />
  <nav class="menu">
    <a :key="i" v-for="(menu, i) in menus">{{ menu }}</a>
  </nav>
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
      <button
        @click="
          () => {
            setModalInfo(i);
            modalShowHandler(true);
          }
        "
      >
        모달창 열기
      </button>
    </div>
  </div>
</template>

<script>
import Modal from "./components/Modal.vue";
import { productsData } from "./constants/products";

export default {
  name: "App",
  components: {
    Modal,
  },
  data() {
    return {
      menus: ["Home", "Products", "About"],
      products: productsData,
      modal: {
        showYN: false,
        index: 0,
      },
    };
  },
  methods: {
    changeCounter(i) {
      this.products[i].count++;
    },
    setModalInfo(index) {
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

.menu {
  margin: 0 auto;
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  cursor: pointer;
  padding: 10px;
}

.menu a:hover {
  font-weight: 600;
}

.room img {
  width: 500px;
  margin-top: 40px;
}
</style>
