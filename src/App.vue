<template>
  <div id="app">
    <AppHeader />
    <b-container>
      <b-row class="justify-content-center">
        <AddProduct />
        <ListProduct />
      </b-row>
    </b-container>
  </div>
</template>

<script>
import AppHeader from '@/components/AppHeader'
import ListProduct from '@/components/ListProduct'
import AddProduct from '@/components/AddProduct'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    AppHeader,
    AddProduct,
    ListProduct
  },
  data(){
    return{
      productList: []
    }
  },
  methods: {
    async getProductList(){
      try {
        let result = await axios.get('http://localhost:3000/products')
        console.log(result.data)
        this.productList = result.data
      } catch (error) {
        console.log(error)
      }
    }
  },
  mounted(){
    this.getProductList();
  }
}
</script>

<style>
.error-message{
  color: crimson;
}
</style>
