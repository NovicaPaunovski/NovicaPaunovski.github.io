<template>
  <main class="flex flex-row min-w-screen min-h-screen bg-dark-palette">
      <Sidebar />
      <div id="body" class="w-full text-slate-200">
        <slot /> 
      </div>
    </main>
</template>

<style scoped>
.bg-dark-palette {
  background-color: #313338;
}

  #body {
    @media (max-width: 768px) {
      padding-left: 6rem;
    }
  }
</style>