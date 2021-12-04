<template>
  <div
    class="m-0 p-0 min-h-screen flex items-center justify-center bg-gray-100 text-center"
  >
    <div class="max-w-md w-full space-y-8">
      <div class="mb-12">
        <h2 class="mt-6 text-center text-4xl font-extrabold text-gray-900 border-b border-gray-300 pb-4">
          Sign Up
        </h2>
      </div>

      <Signupform />
    </div>
  </div>
</template>

<script>
import Signupform from "./components/Signupform.vue"

export default {
  name: "App",
  components: {
    Signupform,
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
