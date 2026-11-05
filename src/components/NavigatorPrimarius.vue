<script setup lang="ts">
import { House, Menu } from '@lucide/vue'
import { ref, onMounted, onUnmounted } from 'vue'

import {
  NavigationMenu,
  NavigationMenuItem,
  NavigationMenuLink,
  NavigationMenuList,
  navigationMenuTriggerStyle,
} from '@/components/ui/navigation-menu'

import { Toggle } from '@/components/ui/toggle'

interface MenuItem {
  label: string
  href: string
  onClick: () => void
}

defineProps<{
  items: MenuItem[]
  homeRoute: string
}>()

const videreMenu = ref<boolean>(true)

const handleResize = () => {
  videreMenu.value = window.innerWidth >= 640
}

onMounted(() => {
  handleResize()
  window.addEventListener('resize', handleResize)
})

onUnmounted(() => {
  window.removeEventListener('resize', handleResize)
})
</script>

<template>
  <Toggle
    class="fixed top-2 right-4 z-50 bg-slate-500 sm:hidden"
    @click="videreMenu = !videreMenu"
    aria-label="Mostra o nascondi menu"
  >
    <Menu :size="46" />
  </Toggle>

  <nav
    v-if="videreMenu"
    class="extra-nav flex flex-col sm:flex-row justify-between px-3"
  >
    <RouterLink :to="homeRoute">
      <House class="icon-home" />
    </RouterLink>

    <NavigationMenu>
      <NavigationMenuList class="flex flex-col sm:flex-row">
        <NavigationMenuItem
          v-for="item in items"
          :key="item.href"
        >
          <a :href="item.href" @click.prevent="item.onClick()">
            <NavigationMenuLink
              :class="[
                navigationMenuTriggerStyle(),
                'text-md hover:bg-brand-purple hover:text-white transition-colors',
              ]"
            >
              {{ item.label }}
            </NavigationMenuLink>
          </a>
        </NavigationMenuItem>
      </NavigationMenuList>
    </NavigationMenu>
  </nav>
</template>

<style scoped>
.icon-home {
  color: slateblue;
  width: 3rem;
  height: 3rem;
}

.icon-home:hover {
  color: white;
  background-color: slateblue;
}

.extra-nav {
  background-color: white;
  opacity: 0.7;
  position: fixed;
  top: 0;
  width: 11rem;
  border-radius: 0 0 1rem 0;
  z-index: 1;
}

@media (min-width: 640px) {
  .extra-nav {
    width: 100%;
    border-radius: 0;
    opacity: 1;
    left: 0;
  }
}
</style>