<template>
  <div class="profile">
    <div class="text-center" v-if="show_info">
      <div class="p-2 bg-green-800 items-center text-green-100 leading-none lg:rounded-full flex lg:inline-flex" role="alert">
        <span class="flex rounded-full bg-green-500 uppercase px-2 py-1 text-xs font-bold mr-3">Saved</span>
        <span class="mr-2 text-left flex-auto">Name saved successfully. Go to Home to check it!</span>
      </div>
    </div>

    <div class="border border-green-300 shadow rounded-md mt-4 p-4 max-w-sm w-full mx-auto" v-if="loading">
      <div class="animate-pulse flex space-x-4">
        <div class="flex-1 space-y-4 py-1">
          <div class="h-4 bg-green-400 rounded w-3/4"></div>
          <div class="space-y-2">
            <div class="h-4 bg-green-400 rounded"></div>
            <div class="h-4 bg-green-400 rounded w-5/6"></div>
          </div>
        </div>
      </div>
    </div>

    <iframe src="http://localhost:8081" class="w-screen" @load.once="loading = !loading"></iframe>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show_info: false,
      loading: true
    }
  },
  mounted() {
    window.addEventListener("message", this.iframeEvent, false)
  },
  beforeDestroy() {
    window.removeEventListener("message", this.iframeEvent, false)
  },
  methods: {
    iframeEvent(event) {
      if (event.data) {
        if (event.origin != 'http:://localhost:8081') {
          let data = JSON.parse(event.data)
          window.localStorage.setItem('name', data.name)
          this.show_info = true
        }
      }
    },
  },
}
</script>

<style scoped>
.loading {
  width: 32px;
  height: 32px;
  background: black;
  animation: pulse 1.5s cubic-bezier(0.4, 0, 0.6, 1) infinite;
  border-radius: 50%;
}

@keyframes pulse {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: .5;
  }
}
</style>