<template>
  <div class="black-bg" v-if="modal.showYN">
    <div class="white-bg">
      <h4>{{ modal.title }}</h4>
      <p v-html="modal.content" />
      <button @click="modalClose">모달창 닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ModalComponent",
  props: {
    modal: {
      type: {
        showYN: Boolean,
        title: String,
        content: String,
      },
      default: {
        showYN: false,
        title: "타이틀",
        content: "내용",
      },
    },
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
