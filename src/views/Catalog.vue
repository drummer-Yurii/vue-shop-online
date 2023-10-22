<template>
  <div class="products-list">
    <div 
        class="product" 
        v-for="product in store.products" 
        :key="product.id"
    >
      <img :src="product.thumbnail" alt="img" />
      <h2>Brand: {{ product.brand }}</h2>
      <p>Description: {{ product.description }}</p>
      <p>Price: ${{ product.price }}</p>
    </div>
  </div>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'CatalogView'
})
</script>

<script setup>
import { onMounted } from 'vue'
import { productsStore } from '@/stores/products'

const store = productsStore()

onMounted(async () => {
    await store.fetchProductsFromDB();

    console.log('MOUNTED!!!!!!!!!!!', store.products);
})
</script>

<style scoped></style>
