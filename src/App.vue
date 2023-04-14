<template>
  <div class="menu">
    <a v-for="(menu, i) in menus" :key="i">{{ menu }}</a>
  </div>

  <div>
    <img src="./assets/room0.jpg" class="room-img" />
    <h4>{{ products[0] }}</h4>
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
</style>
