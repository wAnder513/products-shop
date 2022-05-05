<template>
  <div class="product-description">
    <div>
      <div>
        <div>Название товара</div>
        <div></div>
      </div>

      <div calss="product-description_container">
        <div class="product-description_right">
          <div class="product-description_counter">
            Количество
          </div>
          <div>
            Стоимость
          </div>
        </div>
      </div>
    </div>

    <hr class="product-description-hr" />

    <product-save-button @send-order="sendOrder"></product-save-button>
  </div>
</template>

<script>
import ProductSaveButton from './ProductSaveButton.vue'

export default {
  components: { ProductSaveButton },
  props: {
    selectedProducts: { type: Array }
  },
  methods: {
    sendOrder () {
      this.$emit('send-order')
    }
  }
}
</script>

<style scoped>
.product-description {
  width: calc(100% - 50px);
}

.product-description-wrapper {
  display: flex;
  justify-content: space-between;
  width: calc(100% - 50px);
}

.product-description_counter {
  margin-right: 50px;
}

.product-description_right {
  display: flex;
  margin-bottom: 260px;
}

.product-description-hr {
  border-color: #2fa6ea;
  width: 100%;
  height: 1px;
  margin-bottom: 65px;
}

.product-description_container {
  width: 100%;
}
</style>
