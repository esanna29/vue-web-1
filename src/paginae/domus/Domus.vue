<script setup lang="ts">
import Button from '@/components/ui/button/Button.vue';
</script>
<template>
  <div class="bg-domus-navy h-screen text-white font-sans text-center flex flex-col items-center justify-center gap-12">
 <img class="absolute" src="/imagines/tonitrus1.png" alt="" />
  <h1 class="text-5xl md:text-7xl lg:text-8xl font-bold pb-5 md:pb-20 z-10 transition-all">
  <span class="text-domus-cyan">Diseño</span> Web y<br />
  Apps <span class="text-domus-cyan">Interactivas</span>
</h1>
<p class="text-lg md:text-2xl transition-all">
  Aprendiendo a crear aplicaciones web
</p>
    <div class="scale-90">
      <Button variant="domus" class="mr-2.5">
        <RouterLink to="/batman">Batman</RouterLink>
      </Button>
      <Button variant="domus" class="mr-2.5">
  <RouterLink to="/simpsons">Simpsons</RouterLink>
</Button>
<Button variant="domus" class="mr-2.5">
  <a href="https://www.upv.es">UPV</a>
</Button>
    </div>
  </div>
</template>
<style scoped>
.fondo-home {
  background-color: rgb(21, 25, 52);
  height: 100vh;
  color: rgb(24, 182, 246);
}
.botones > Button {
  background-color: rgba(24, 182, 246, 0.7);
  margin-right: 0.5rem;
}
</style>