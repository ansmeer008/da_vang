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

  <button @click="priceSort">낮은가격순정렬</button>
  <button @click="higherPriceSort">높은가격순정렬</button>
  <button @click="letterSort">알파벳순정렬</button>
  <button @click="sortBack">되돌리기</button>

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
      // showDiscount: true,
      originalProducts: [...data],
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
  //마운트 되자마자 실행하는 라이프사이클 훅
  // mounted() {
  //   setTimeout(() => {
  //     //arrow function 사용해주는 게 this를 더 잘 활용할 수 있음
  //     this.showDiscount = false;
  //   }, 2000);
  // },
  methods: {
    increase(i) {
      this.reportCount[i]++;
    },
    priceSort() {
      this.products.sort((a, b) => {
        return a.price - b.price;
      });
    },
    higherPriceSort() {
      this.products.sort((a, b) => {
        return b.price - a.price;
      });
    },
    letterSort() {
      this.products.sort((a, b) => {
        return a.title - b.title;
      });
    },
    sortBack() {
      this.products = [...this.originalProducts];
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
