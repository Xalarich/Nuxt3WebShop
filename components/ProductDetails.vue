<template>
  <div class="card">
    <div class="grid grid-cols-1 gap-10 lg:grid-cols-2">
      <div class="p-7">
        <img :src="product.image" class="mx-auto my-7" />
      </div>
      <div class="p-7">
        <h2 class="text-4xl my-7">{{ product.title }}</h2>
        <p class="text-xl my-7">Price - ${{ product.price }}</p>
        <h3 class="font-bold border-b-2 mb-4 pb-2">Product description:</h3>
        <p class="mb-7">{{ product.description }}</p>
        <button @click="addToCart" class="btn flex">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            height="24"
            viewBox="0 0 24 24"
            width="24"
          >
            <path d="M0 0h24v24H0zm18.31 6l-2.76 5z" fill="none" />
            <path
              d="M11 9h2V6h3V4h-3V1h-2v3H8v2h3v3zm-4 9c-1.1 0-1.99.9-1.99 2S5.9 22 7 22s2-.9 2-2-.9-2-2-2zm10 0c-1.1 0-1.99.9-1.99 2s.89 2 1.99 2 2-.9 2-2-.9-2-2-2zm-9.83-3.25l.03-.12.9-1.63h7.45c.75 0 1.41-.41 1.75-1.03l3.86-7.01L19.42 4h-.01l-1.1 2-2.76 5H8.53l-.13-.27L6.16 6l-.95-2-.94-2H1v2h2l3.6 7.59-1.35 2.45c-.16.28-.25.61-.25.96 0 1.1.9 2 2 2h12v-2H7.42c-.13 0-.25-.11-.25-.25z"
            />
          </svg>
          <div>
            <span v-if="isInCart()">Remove item</span>
            <span v-else>Add to cart</span>
          </div>
        </button>
      </div>
    </div>
  </div>
</template>
<script setup>
const { product } = defineProps(["product"]);
const emit = defineEmits(["myEvent"]);
const cart = useCart();
function isInCart() {
  return !!cart.value.find((ct) => ct.product === product);
}
function addToCart() {
  if (!isInCart()) {
    cart.value.push({
      product,
    });
  } else {
    cart.value = cart.value.filter((ct) => ct.product !== product);
  }
  console.log(cart.value[0]);
}
</script>
<style scoped>
img {
  max-width: 400px;
}
</style>
