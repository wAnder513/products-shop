<template>
  <div id="app">
    <div class="app-header">sf</div>
    <div class="app-container">
      <div class="app-description">
        <product-selection :products="products" @add-products="addProducts">
        </product-selection>

        <product-description
          :selected-products="selectedProducts"
          @send-order="sendOrder"
        ></product-description>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import ProductDescription from './components/ProductDescription.vue'
import ProductSelection from './components/ProductSelection.vue'

export default {
  name: 'App',
  components: { ProductSelection, ProductDescription },
  data () {
    return {
      products: [],
      selectedProducts: []
    }
  },
  created () {
    this.getProducts()
  },
  methods: {
    getProducts () {
      axios.get('https://dev-su.eda1.ru/test_task/products.php').then(res => {
        this.products = res.data.products
      })
    },
    addProducts (product) {
      this.selectedProducts.push(product)
    },
    sendOrder () {
      // send order on back
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

button {
  cursor: pointer;
  border-radius: 5px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #ffffff;
  width: 1440px;
  padding: 0 15px;
  background-color: rgb(177, 177, 14);
}

.app-header {
  background-color: rgb(87, 55, 12);
  color: #ffffff;
  margin: 0 -15px 45px;
  padding: 10px 15px;
}

.app-container {
  background-color: #ffffff;
  color: black;
}

.app-description {
  display: flex;
}
</style>
