<template>
  <header class="border-b">
    <div
      class="container flex flex-col flex-wrap px-8 py-4 md:items-center md:flex-row"
    >
      <nav>
        <ul class="flex flex-wrap items-center justify-center text-base">
          <li class="mr-5 text-sm font-semibold hover:text-gray-800">
            <router-link to="/">Home</router-link>
          </li>
          <li class="mr-5 text-sm font-semibold hover:text-gray-800">
            <router-link to="/profile">Profile</router-link>
          </li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  name: "Navbar",
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
nav li a:hover,
nav li a.router-link-exact-active {
  color: rgb(13, 155, 96);
  cursor: pointer;
}
</style>
