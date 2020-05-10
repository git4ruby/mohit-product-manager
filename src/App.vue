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
export default {
  name: 'App',
  components: {
    AppHeader,
    AddProduct,
    ListProduct
  }
}
</script>

<style>
.error-message{
  color: crimson;
}
</style>
