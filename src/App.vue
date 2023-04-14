<template>
  <div class="backdrop" v-if="isOpen">
    <div class="modal-box">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
      <button v-on:click="isOpen = false">닫을거임</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(menu, i) in menus" :key="i">{{ menu }}</a>
  </div>

  <div>
    <img src="./assets/room0.jpg" class="room-img" />
    <h4 v-on:click="isOpen = true">{{ products[0] }}</h4>
    <p>50 만원</p>
    <button v-on:click="increase(0)">허위매물신고</button>
    <span>신고 수: {{ reportCount[0] }}</span>
  </div>
  <div>
    <img src="./assets/room1.jpg" class="room-img" />
    <h4>{{ products[1] }}</h4>
    <p>가격은 아무거나</p>
    <button v-on:click="increase(1)">허위매물신고</button>
    <span>신고 수: {{ reportCount[1] }}</span>
  </div>
  <div>
    <img src="./assets/room2.jpg" class="room-img" />
    <h4>{{ products[2] }}</h4>
    <p>가격은 아무거나</p>
    <button v-on:click="increase(2)">허위매물신고</button>
    <span>신고 수: {{ reportCount[2] }}</span>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      reportCount: [0, 0, 0],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
      menus: ["Home", "Products", "About"],
      isOpen: false,
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
