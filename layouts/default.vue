<template>
  <header>
    <h1>Nuxt 3</h1>
  </header>
  <main>
    <slot />
  </main>
  <footer>
    <p>
      {{ new Date().getFullYear() }}
    </p>
  </footer>
</template>

<script>
export default {
  name: "default"
}
</script>

<style scoped>

</style>