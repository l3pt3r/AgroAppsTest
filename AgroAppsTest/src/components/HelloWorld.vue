<script setup>
defineProps({
  msg: {
    type: String,
    required: true
  }
})
</script>

<template>
  <div class="greetings">
    <h1>{{ msg }}</h1>
  </div>
</template>

<style scoped>
.greetings h1 {
  text-align: left;
  font-weight: 500;
  font-size: 2.5rem;
  /* top: -10px; */
}

</style>
