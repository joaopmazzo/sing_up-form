<template>
  <singu-up-view />
</template>

<script>
import Singup from './views/Singup.vue';

export default {
  components: {
    "singu-up-view": Singup,
  },
  name: "app",
}
</script>

<style>
*{
  color: #fff;
}
</style>