<script setup>
import { ref } from 'vue'

const props = defineProps({
  openSidebar: {
    type: Boolean,
    required: true
  }
})

const links = ref([
  {name: 'Типографика', href: '/typography'},
  {name: 'Кнопки', href: '/button'},
  {name: 'Чекбокс', href: '/checkbox'},
  {name: 'Радио кнопка', href: '/radio'},
  {name: 'Инпут', href: '/input'},
  {name: 'Прогресс', href: '/progress'},
  {name: 'Табы', href: '/tabs'},
  {name: 'Таблица', href: '/table'},
])
</script>

<template>
  <div :class="['sidebar', {'sidebar--open': openSidebar}]">
    <router-link 
      class="sidebar__link"
      v-for="link in links" 
      :key="link.name"
      :to="link.href">{{ link.name }}</router-link>
  </div>
</template>	

<style lang="scss" scoped>
.sidebar {
  left: 0;
  top: 62px;
  height: 100%;
  background-color: #fff;
  position: fixed;
  width: 250px;
  padding: 20px;
  transition: .2s;
  box-shadow: 0 0 10px rgba(0,0,0,.07);
  transform: translateX(-250px);
  &--open {
    transform: translateX(0);
  }
  &__link {
    display: block;
    transition: .2s;
    font-weight: bold;
    margin-bottom: 10px;
    &:hover {
      color: var(--primary-h);
    }
  }
}
</style>
