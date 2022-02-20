<template>
  <app-layout title="Home" :showcase-url="showcase">
    <template #header>
      <h1 class="mb-8 text-6xl text-gray-50 text-center font-poppins font-bold">
        <span class="uppercase">Bapa Hotel Colonial</span>
      </h1>
      <p class="text-white text-center"> Nuestro hotel colonial cuenta con una de las mejores habitaciones disponibles de la Jagua de Ibirico. Contamos además de con centro de eventos, restaurante y bar. </p>
    </template>
  </app-layout>
</template>

<script>
import { Link } from "@inertiajs/inertia-vue3";
import AppLayout from "@/Layouts/GuestLayout.vue";

export default {
  components: {
    Link,
    AppLayout,
  },
  props: ["showcase"],
  mounted() {
    console.log(this.showcase);
  },
};
</script>
