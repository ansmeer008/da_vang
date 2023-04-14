<template>
  <div>
    <!-- html 태그 안의 속성 데이터 바인딩은 ':' 붙여줘야 함 -->
    <img :src="product.image" class="room-img" />
    <h4>
      {{ product.title }}
    </h4>
    <p>{{ product.price }}</p>
  </div>
</template>

<script>
export default {
  name: "ItemCard",
  props: {
    product: Object,
  },
};
</script>

<style></style>
