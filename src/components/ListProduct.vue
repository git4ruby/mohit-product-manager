<template>
  <b-col md="4" class="m-3">
    <b-card header="List Product">
      <b-card-group deck>
        <b-card
          style="min-width: 50%"
          class="m-3"
          :border-variant="product.inventoryStatus? 'success':'danger'"
          align="center"
          v-for="product in products" :key="product.id"
        >
          <b-badge class="mb-3" :variant="product.inventoryStatus? 'success':'danger'">{{ product.inventoryStatus? 'IN STOCK':'OUT OF STOCK' }}</b-badge>
          <b-card-text><strong>Name: </strong>{{ product.name }}</b-card-text>
          <b-card-text><strong>Price: </strong>{{ product.price }}</b-card-text>
          <b-card-text><strong>Brand: </strong>{{ product.brand }}</b-card-text>
        </b-card>
      </b-card-group>
    </b-card>
  </b-col>
</template>

<script>
export default {
  props: ['products']
}
</script>

<style>

</style>