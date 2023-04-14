<template>
  <div class="backdrop" v-if="isOpen">
    <div class="modal-box">
      <h4>{{ products[clickedProduct].title }}</h4>
      <img class="room-img" :src="products[clickedProduct].image" />
      <p>{{ products[clickedProduct].content }}</p>
      <!-- input 이벤트는 input에 뭐 입력할 때마다 감지해주는 이벤트 -->
      <!-- <input v-on:input="month = $event.target.value" /> -->
      <!-- 위 코드를 아래와 같이 축약할 수도 있다. -->
      <input v-model.number="month" />
      <!-- v-model로 input에 들어온 데이터를 저장하면 모두 문자열로 저장되므로, 숫자로 저장하고 싶을 때는 
      v-model.number="month"와 같이 작성해줄 수 있다. -->
      <p>
        {{ month }} 개월 선택함 : {{ products[clickedProduct].price * month }}
      </p>
      <!-- props는 readOnly라 받아온 props를 변화시키면 안 된다 -->
      <button v-on:click="$emit('closeModal')">닫을거임</button>
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
  data() {
    return {
      month: 1,
    };
  },
  watch: {
    month(a) {
      if (a >= 13) {
        alert("12까지만 입력할 수 있어욥!");
      }
      if (typeof a === "string") {
        alert("숫자만 입력해주세요!");
      }
    },
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
