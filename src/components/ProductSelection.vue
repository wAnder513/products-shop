<template>
  <div class="product-selection">
    <div class="product-selection_text">Выбирите продукцию</div>
    <select @change="addProductValue" class="product-selection_input">
      <template v-if="hasProducts">
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
    <button class="product-selection_button" @click="addProduct">
      Добавить
    </button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      currentProduct: null,
      currentCounter: 0
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
      this.$emit('add-products', {
        currentProduct: this.currentProduct,
        currentCounter: this.currentCounter
      })
    },
    addProductValue (e) {
      this.currentProduct = e.target.value
    },
    addCurrentCounter (e) {
      this.currentCounter = e.target.value
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
  font-size: 20px;
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
  font-size: 20px;
}
</style>
