<template>
  <div class="product-button">
    <button class="product-button_save" @click="sendOrder">Сохранить</button>
  </div>
</template>

<script>
export default {
  methods: {
    sendOrder () {
      this.$emit('send-order')
    }
  }
}
</script>

<style scoped>
.product-button {
  display: flex;
  justify-content: center;
}

.product-button_save {
  background-color: #61a91a;
  color: #fff;
  width: 400px;
  padding: 10px 15px;
}
</style>
