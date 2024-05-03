<template>
    <div>
      <header class="shadow-sm bg-white">
           <nav class="container mx-auto p-4 flex justify-between items-center">
              <NuxtLink to="/" class="font-bold flex gap-2 items-center mr-5">
                <img class="w-48 min-w-24" src="../assets/content/logo.svg"/>
              </NuxtLink>
              <ul class="flex gap-4 items-center">
                  <li><NuxtLink to="/"><p class="text-lg">Home</p></NuxtLink></li>
              </ul>
          </nav>
      </header>
      <div class="container mx-auto p-4">
        <slot />
      </div>
      
      <footer>

      </footer>
  </div>
</template>

<style scoped>
  .router-link-exact-active {
    color: #12b488;
  }
</style>