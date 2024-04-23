<template>
  <Modal :modal="modal" @modal="modalShowHandler" />
  <nav class="menu">
    <a :key="i" v-for="(menu, i) in menus">{{ menu }}</a>
  </nav>
  <div>
    <h1>원룸샵</h1>
    <div class="room" :key="i" v-for="(product, i) in products">
      <img :src="require(`./assets/rooms/room${i}.jpg`)" alt="room" />
      <h4>{{ product.name }}</h4>
      <p>{{ product.price }} 만원</p>
      <!-- (v-on:click = @click) = "자바스크립트 문법을 넣는다." -->
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

export default {
  name: "App",
  components: {
    Modal,
  },
  // 데이터 보관함
  data() {
    return {
      menus: ["Home", "Products", "About"],
      products: [
        {
          name: "역삼동원룸",
          price: 60,
          count: 0,
        },
        {
          name: "천호동원룸",
          price: 30,
          count: 0,
        },
        {
          name: "마포구원룸",
          price: 100,
          count: 0,
        },
      ],
      modal: {
        showYN: false,
        title: "",
        content: "",
      },
    };
  },
  methods: {
    changeCounter(i) {
      this.products[i].count++;
    },
    setModalInfo(index) {
      this.modal.title = this.products[index].name;
      this.modal.content = `<div><p>해당 매물의 가격은 ${this.products[index].price}만원입니다.</p><p>해당 매물의 허위 매물 신고 건수는 ${this.products[index].count}건입니다.</p></div>`;
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
