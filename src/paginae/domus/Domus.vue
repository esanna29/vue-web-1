<script setup lang="ts">
import Button from '@/components/ui/button/Button.vue';
import {
  Dialog,
  DialogContent,
  DialogDescription,
  DialogHeader,
  DialogTitle,
  DialogTrigger,
} from '@/components/ui/dialog'
import { Input } from '@/components/ui/input'
import { ref } from 'vue'

const dialogApertaEst = ref<boolean>(false)
const quaestio = ref<string>('')
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
      <Dialog
  :open="dialogApertaEst"
  @update:open="dialogApertaEst = $event"
>
  <DialogTrigger as-child>
    <Button variant="domus" class="mr-2">
      Sí o no
    </Button>
  </DialogTrigger>

  <DialogContent class="sm:max-w-[425px] bg-domus-navy text-white border-domus-cyan">
    <DialogHeader>
      <DialogTitle class="text-white">Pregúntame</DialogTitle>
      <DialogDescription class="text-gray-300">
        No sigas con tus dudas, yo te responderé SÍ o NO.
      </DialogDescription>
    </DialogHeader>

    <div class="mt-4">
      <Input
        class="bg-domus-navy-input text-white placeholder:text-gray-400"
        placeholder="Escribe aquí tu pregunta..."
        v-model="quaestio"
      />
    </div>
  </DialogContent>
</Dialog>
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