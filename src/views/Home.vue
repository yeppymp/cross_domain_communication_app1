<template>
  <div class="home p-8 text-center">
    <h4 class="font-bold">Hello, {{ name }}!</h4>
    <p class="text-justify mt-2 text-gray-500">
      This app is implementing Cross Domain Communication (or Cross-Origin). Profile page is in
      another project which wrapped by iFrame. The idea is when user update the name
      from Profile page (another project) the name will be saved to local
      storage and when you go back to Home, et voila! the name is changed.
    </p>
    <p class="mt-8">
      Made with
      <img alt="Vue logo" src="../assets/logo.png" class="inline-block h-4" />
    </p>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      name: "Chief",
    };
  },
  mounted() {
    this.checkCachedName();
  },
  methods: {
    checkCachedName() {
      let name_cache = window.localStorage.getItem("name");

      if (name_cache) {
        this.name = name_cache;
      }
    },
  },
};
</script>
