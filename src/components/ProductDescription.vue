<template>
  <div class="product-description">
    <div class="product-description_wrapper">
      <div class="product-description_container">
        <div>Название товара</div>
        <div class="product-description_right">
          <div class="product-description_counter">
            Количество
          </div>
          <div>
            Стоимость
          </div>
        </div>
      </div>

      <template v-if="hasSelectedProducts">
        <product-description-order
          v-for="product in selectedProducts"
          :key="product.id"
          :product="product"
        >
        </product-description-order>
      </template>
    </div>
    <hr class="product-description-hr" />

    <product-save-button @send-order="sendOrder"></product-save-button>
  </div>
</template>

<script>
import ProductDescriptionOrder from './ProductDescriptionOrder.vue'
import ProductSaveButton from './ProductSaveButton.vue'

export default {
  components: { ProductSaveButton, ProductDescriptionOrder },
  props: {
    selectedProducts: { type: Array }
  },
  computed: {
    hasSelectedProducts () {
      return this.selectedProducts && this.selectedProducts.length > 0
    }
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

.product-description_wrapper {
  margin-bottom: 260px;
}

.product-description_right {
  display: flex;
}

.product-description-hr {
  border-color: #2fa6ea;
  width: 100%;
  height: 1px;
  margin-bottom: 65px;
}

.product-description_order {
  display: flex;
  justify-content: space-between;
}

.product-description_container {
  display: flex;
  justify-content: space-between;
  width: 100%;
  margin-bottom: 20px;
  color: #2fa6ea;
}
</style>
