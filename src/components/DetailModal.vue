<template>
  <div class="backdrop" v-if="isOpen">
    <div class="modal-box">
      <h4>{{ products[clickedProduct].title }}</h4>
      <img class="room-img" :src="products[clickedProduct].image" />
      <p>{{ products[clickedProduct].price }}</p>
      <p>
        {{ products[clickedProduct].content }}
      </p>
      <!-- props는 readOnly라 받아온 props를 변화시키면 안 된다 -->
      <!-- <button v-on:click="isOpen = false">닫을거임</button> -->
    </div>
  </div>
</template>

<script>
export default {
  name: "DetailModal",
  props: {
    products: Array,
    clickedProduct: Number,
    isOpen: Boolean,
  },
};
</script>

<style>
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
