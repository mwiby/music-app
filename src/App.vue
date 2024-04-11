<script setup lang="ts">
import { ref, onMounted } from "vue"
import { RouterLink, RouterView } from "vue-router"

import MenuItem from "./components/MenuItem.vue"

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

    <div class="side-bar">
      <RouterLink to="/">
        <span>IMG</span>
        <!--<img class="logo" src="/images/icons/spotify-logo.png" alt="Spotify Logo" width="125"> -->
      </RouterLink>
      <div class="spacer"></div>
      <ul>
        <RouterLink to="/">
          <MenuItem class="menu-item" :iconSize="23" name="Home" iconString="home" pageUrl="/" />
        </RouterLink>
        <RouterLink to="/search">
          <MenuItem class="menu-item" :iconSize="24" name="Search" iconString="search" pageUrl="/search" />
        </RouterLink>
        <RouterLink to="/library">
          <MenuItem class="menu-item" :iconSize="23" name="Your Library" iconString="library" pageUrl="/library" />
        </RouterLink>
          <div class="spacer-y"></div>
          <MenuItem class="menu-item" :iconSize="24" name="Create Playlist" iconString="playlist" pageUrl="/playlist" />
          <MenuItem class="menu-item" :iconSize="27" name="Liked Songs" iconString="liked" pageUrl="/liked" />
      </ul>
      <div class="divider"></div>
      <ul>
        <li class="playlist">My Playlist #1</li>
        <li class="playlist">My Playlist #2</li>
        <li class="playlist">Topp Playlist #3</li>
        <li class="playlist">Global Playlist #4</li>
      </ul>
    </div>
  </div>

  <div>
    <div></div>
      <RouterView />
    <div></div>
  </div>

    <!-- <MusicPlayer v-if="currentTrack"/> -->
</template>

<style lang="scss" scoped>
@import "@/assets/styles.scss";

.top-bar {
  width: calc(100% - 330px); 
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
      list-style-type: none;
      
      &:hover {
        background-color: #3E3D3D;
      }

      &:not(:last-child) {
        border-bottom: 1px solid $primary-grey;
      }
    }
  }
}
.side-bar {
  width: 250px;
  background-color: $secondary-color;
  color: $primary-color;
  padding: 20px;
  height: 100vh;
  position: fixed;
  top: 0;
  left: 0;

  ul {
    list-style: none;
    padding: 0;
    margin: 0;

    .menu-item {
      display: flex;
      align-items: center;
      padding: 10px;
      cursor: pointer;
      transition: background-color 0.3s ease;

      &:hover {
        background-color: $primary-grey;
      }

      span {
        margin-left: 10px;
      }
    }

    .spacer,
    .spacer-y {
      height: 20px;
    }

    .divider {
      height: 1px;
      background-color: #383838;
      margin: 20px 0;
    }

    .playlist {
      padding: 10px;
      cursor: pointer;

      &:hover {
        background-color: $primary-grey;
      }
    }
  }
}
</style>
