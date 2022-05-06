<template>
  <div class="product-description-order">
    <div>{{ product.currentProduct }}</div>
    <div class="product-description-order_right">
      <div class="product-description-order_counter">
        {{ product.currentCounter }} шт.
      </div>
      <div>{{ product.currentPrice }}</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    product: { type: Object }
  }
}
</script>

<style scoped>
.product-description-order {
  display: flex;
  justify-content: space-between;
}

.product-description-order_right {
  display: flex;
}

.product-description-order_counter {
  margin-right: 105px;
}
</style>
