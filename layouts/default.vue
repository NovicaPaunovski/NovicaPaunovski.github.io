<template>
  <main class="flex flex-row min-w-screen min-h-screen">
      <Sidebar />
      <div id="body" class="w-full text-neutral-800">
        <slot />
      </div>
    </main>
</template>

<style scoped>
  #body {
    @media (max-width: 768px) {
      padding-left: 6rem;
    }
  }
</style>