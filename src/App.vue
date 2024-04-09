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
                <div class="btn-chevron-bar">
                    <img 
                      src="https://images.pexels.com/photos/1105666/pexels-photo-1105666.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
                    >
                    <span>Markus</span>
                    <i class="chevron-down" v-if="!openMenu" @click="openMenu = true"></i>
                    <i class="chevron-up" v-else @click="openMenu = false"></i>
                </div>
      </button>

      <span v-if="openMenu" class="menu-container">
        <ul class="menu-list">
          <li class="menu-item">Profile</li>
          <li class="menu-item">Log out</li>
        </ul>
      </span>
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
  display: inline-flex;
  align-items: center;
  appearance: none;
  border: none;
  padding: 0;
  background: none;
  font-family: inherit; 
  font-size: inherit; 
  margin-left: 1.2rem;
  cursor: pointer;
}

.btn-chevron-bar{
  background-color:$primary-grey;
  padding: 0 0.4rem;
  color: $text-color;
  border-radius: 45%;

  span{
    margin: 0.5rem;
  }
  img{
    margin-top: 5px;
    border-radius: 50%;
    width: 20px;
  }
  i{
    margin-bottom: 0.2rem;
  }

}
.menu-container {
  position: fixed;
  background-color:$secondary-color;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  z-index: 50;
  border-radius: 0.25rem;
  top: 52px;
  right: 35px;
  padding: 0.25rem;
  cursor: pointer;
  width: 190px;

  .menu-list {
    color: $primary-color;
    font-weight: 600;
    font-size: 14px;
    
    li {
      padding: 0.75rem 1rem;
      cursor: pointer;

      &:hover {
        background-color: #3E3D3D;
      }

      &:not(:last-child) {
        border-bottom: 1px solid $primary-grey;
      }
    }
  }
}
</style>
