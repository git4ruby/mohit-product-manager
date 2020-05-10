<template>
  <div id="app">
    <AppHeader />
    <b-container>
      <b-row class="justify-content-center">
        <AddProduct @addProduct="addProduct"/>
        <ListProduct :products="productList" @deleteProduct="deleteProduct" @updateProduct="updateProduct"/>
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
    },
    async addProduct(newProduct){
      try {
        await axios.post('http://localhost:3000/products', newProduct)
        this.getProductList()
      } catch(error) {
        console.log(error)
      }
      console.log(newProduct)
    },
    async deleteProduct(productId){
      try {
        // await axios.delete('http://localhost:3000/products/'+ productId)
        await axios.delete(`http://localhost:3000/products/${productId}`)
        this.getProductList()
      } catch(error) {
        console.log(error)
      }
      console.log(productId)
    },
    async updateProduct(updatedProduct){
      try {
        await axios.put(`http://localhost:3000/products/${updatedProduct.id}`, updatedProduct)
        this.getProductList()
      } catch(error){
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
