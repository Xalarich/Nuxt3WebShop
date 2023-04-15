<script setup>
definePageMeta({
  layout: "products",
});
const { data: products } = await useFetch("https://fakestoreapi.com/products");
</script>
<template>
  <div class="flex flex-row">
    <div>
      <div class="grid grid-cols-2 sm:grid-cols-4 gap-5">
        <div v-for="p in products" :key="p.id">
          <ProductCard :product="p" />
        </div>
      </div>
    </div>
  </div>
</template>
<style scoped></style>
