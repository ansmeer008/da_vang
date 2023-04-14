<template>
  <transition name="fade">
    <DetailModal
      v-bind:products="products"
      v-bind:clickedProduct="clickedProduct"
      v-bind:isOpen="isOpen"
      v-on:closeModal="isOpen = false"
    />
  </transition>

  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>

  <Discount />

  <ItemCard
    v-on:openModal="
      isOpen = true;
      clickedProduct = $event;
    "
    v-bind:product="products[i]"
    v-for="(product, i) in products"
    :key="product"
  />
</template>

<script>
import data from "./data";
import Discount from "./components/Discount.vue";
import DetailModal from "./components/DetailModal.vue";
import ItemCard from "./components/ItemCard.vue";

export default {
  name: "App",
  data() {
    return {
      reportCount: [0, 0, 0],
      products: data,
      menus: ["Home", "Products", "About"],
      isOpen: false,
      clickedProduct: 0,
    };
  },
  components: {
    Discount: Discount,
    DetailModal: DetailModal,
    ItemCard: ItemCard,
  },
  methods: {
    increase(i) {
      this.reportCount[i]++;
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

body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
.room-img {
  width: 100%;
  margin-top: 40px;
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
</style>
