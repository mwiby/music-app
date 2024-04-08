<script setup lang="ts">
import { ref, onMounted } from "vue"
import { RouterLink, RouterView } from "vue-router"

let openMenu = ref(false)
</script>

<template>

  <div>
    <div class="top-bar">
      <div class="flex-container">
        <button type="button" class="btn-chevron">
          <i class="chevron-left"></i>
        </button>
        <button type="button" class="btn-chevron">
          <i class="chevron-right"></i>
        </button>
      </div>
      <button @click="openMenu = !openMenu" :class="openMenu ? 'bg-[#282828]' : 'bg-black'"
                class="btn-chevron">
                <div class="flex items-center">
                    <img 
                      class="rounded-full" 
                      width="27"
                      src="https://unsplash.com/photos/black-violin-on-underwater-digital-wallpaper-yO4XF2uC4g0"
                    >
                    <div class="text-white text-[14px] ml-1.5 font-semibold">Markus</div>
                    <i class="chevron-down" v-if="!openMenu" @click="openMenu = true"></i>
                    <i class="chevron-up" v-else @click="openMenu = false"></i>
                </div>
      </button>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "@/assets/styles.scss";

.top-bar {
  width: calc(100% - 240px); 
  height: 60px;
  position: fixed;
  right: 0; 
  z-index: 20;
  background-color: $secondary-color; 
  display: flex; 
  align-items: center; 
  justify-content: space-between; 
  padding: 0 20px; 
  color: $primary-color; 
}
.flex-container {
  display: flex;
  align-items: center;
  margin-left: 1.5rem;
}
.btn-chevron{
  appearance: none;
  border: none;
  padding: 0;
  background: none;
  font-family: inherit; 
  font-size: inherit; 
  margin-left: 1.2rem;
  cursor: pointer; /* Add pointer cursor */
}

</style>
