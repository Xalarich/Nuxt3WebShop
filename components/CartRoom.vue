<template>
  <div class="h-screen text-gray-600 text-lg flex flex-col gap-4 pt-4">
    <div class="headerCart ml-1 flex justify-around font-bold">
      <p>Product</p>
      <p>Price</p>
      <p>Delete</p>
    </div>
    <div v-for="item in cart" class="cartItems flex justify-around">
      <p>{{ item.product.title.slice(0, 10) }}</p>
      <p>{{ item.product.price }}</p>
      <button @click="removeItem(item)" class="btn">x</button>
    </div>
    <div class="footerCart flex justify-around font-bold">
      <p>Total price: {{ totalPrice.toFixed(2) }}</p>
      <button class="btn">Checkout</button>
    </div>
  </div>
</template>

<script setup>
import { ref, watchEffect } from "vue";
const cart = useCart();
function removeItem(item) {
  cart.value = cart.value.filter((ct) => ct !== item);
}
const totalPrice = ref(0);
watchEffect(() => {
  totalPrice.value = cart.value.reduce(
    (sum, obj) => sum + obj.product.price,
    0
  );
});
</script>

<style scoped></style>
