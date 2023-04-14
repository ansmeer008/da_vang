<template>
  <div class="backdrop" v-if="isOpen">
    <div class="modal-box">
      <h4>{{ products[clickedProduct].title }}</h4>
      <img class="room-img" :src="products[clickedProduct].image" />
      <p>{{ products[clickedProduct].price }}</p>
      <p>
        {{ products[clickedProduct].content }}
      </p>
      <button v-on:click="isOpen = false">닫을거임</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>

  <div v-for="(room, i) in products" :key="room.id">
    <!-- html 태그 안의 속성 데이터 바인딩은 ':' 붙여줘야 함 -->
    <img :src="room.image" class="room-img" />
    <h4
      v-on:click="
        isOpen = true;
        clickedProduct = i;
      "
    >
      {{ room.title }}
    </h4>
    <p>{{ room.price }}</p>
  </div>
</template>

<script>
import data from "./data";

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
  components: {},
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
.backdrop {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.modal-box {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>
