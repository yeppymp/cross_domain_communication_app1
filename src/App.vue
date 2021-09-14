<template>
  <div id="app" class="bg-green-100 h-screen">
    <navbar/>

    <router-view/>
  </div>
</template>

<script>
// @ is an alias to /src
import Navbar from '@/components/Navbar.vue'

export default {
  components: {
    Navbar
  }
}
</script>

<style></style>
