<template>
  <nav class="menu">
    <a :key="i" v-for="(menu, i) in menus">{{ menu }}</a>
  </nav>
</template>

<script>
export default {
  name: "Navbar",
  data() {
    return { menus: ["Home", "Products", "About"] };
  },
};
</script>

<style>
.menu {
  margin: 0 auto;
  background: darkslateblue;
  padding: 15px;
}

.menu a {
  color: white;
  cursor: pointer;
  padding: 10px;
}

.menu a:hover {
  font-weight: 600;
}
</style>
