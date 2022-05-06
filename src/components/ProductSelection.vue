<template>
  <div class="product-selection">
    <div class="product-selection_text">Выбирите продукцию</div>
    <select
      class="product-selection_input"
      value="somthing"
      @change="addProductValue"
    >
      <template v-if="hasProducts">
        <option value="">Выбирите продукт</option>
        <option
          v-for="product in products"
          :key="product.id"
          :value="product.title"
          >{{ product.title }}</option
        >
      </template>
    </select>

    <div class="product-selection_text">Выбирите количество</div>
    <input
      class="product-selection_input"
      type="number"
      :value="currentCounter"
      @change="addCurrentCounter"
    />
    <button
      class="product-selection_button"
      :disabled="isDisableButtonAdd"
      @click="addProduct"
    >
      Добавить
    </button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      selectedValue: null,
      currentProduct: null,
      currentCounter: 0,
      currentPrice: 0,
      isDisableButtonAdd: true
    }
  },
  props: {
    products: { type: Array }
  },
  computed: {
    hasProducts () {
      return this.products && this.products.length > 0
    }
  },
  methods: {
    addProduct () {
      if (this.currentProduct && this.currentCounter > 0) {
        let priceProduct = 0

        this.products.forEach(product => {
          if (product.title === this.currentProduct) {
            priceProduct = product.price * this.currentCounter
          }
        })

        this.$emit('add-products', {
          currentProduct: this.currentProduct,
          currentCounter: this.currentCounter,
          currentPrice: priceProduct
        })
      }
    },
    addProductValue (e) {
      if (e.target.value !== '') {
        this.isDisableButtonAdd = false
        this.currentProduct = e.target.value
      } else {
        this.isDisableButtonAdd = true
      }
    },
    addCurrentCounter (e) {
      if (e.target.value > 0) {
        this.currentCounter = e.target.value
      }
    }
  }
}
</script>

<style scoped>
.product-selection {
  width: 400px;
  margin-right: 50px;
}

.product-selection_input {
  width: 100%;
  padding: 10px 15px;
  background-color: #eef8ff;
  color: #0170ae;
  border: 1px solid #000000;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  margin-bottom: 40px;
}

.product-selection_text {
  margin-bottom: 20px;
}

.product-selection_button {
  width: 100%;
  background-color: #2fa6ea;
  color: #fff;
  padding: 10px 15px;
}

.product-selection_button:disabled {
  background-color: gray;
  cursor: not-allowed;
}
</style>
