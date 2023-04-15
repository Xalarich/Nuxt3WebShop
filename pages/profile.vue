<template>
  <div class="flex items-center flex-col gap-4 mx-3 mb-5 mt-10">
    <p class="font-bold text-[#12b488] text-xl truncate">
      Welcome to your profile
    </p>
    <div class="flex items-center flex-col card">
      <p class="heading">Your profile picture:</p>
      <img src="../public/images/hamster.jpg" alt="Profile picture" />
    </div>
    <div class="flex items-center flex-col card">
      <p class="heading">Nickname:</p>
      <p>Mr. John "definitelly not" Hamster</p>
    </div>
    <div class="flex items-center flex-col card">
      <p class="heading">Likings:</p>
      <p>Nuts and grains</p>
    </div>
    <div class="flex items-center flex-col card">
      <p class="heading">Hobbies:</p>
      <p class="max-w-screen-sm text-center">
        I love running on spinning wheel, cardio is important you know? I also
        like browsing the web, but I can only do so incognito! Hamsters aren't
        allowed on the internet. :l
      </p>
    </div>
  </div>
</template>

<script setup>
definePageMeta({
  middleware: ["auth"],

  layout: "products",
});
</script>

<style lang="scss" scoped></style>
