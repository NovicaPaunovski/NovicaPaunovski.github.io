<template>
    <main class="flex flex-row min-w-screen min-h-screen">
      <aside id="sidebar" :class="`${isExpanded ? 'is-expanded' : 'items-center'} sidebar flex flex-col min-h-screen bg-slate-800 text-slate-200 overflow-hidden p-4`">
        <div class="logo mb-4 mt-2 flex flex-row justify-between items-center">
            <NuxtLink to="/">
              <img :class="`${isExpanded ? 'expanded-width' : 'w-8'}`" src="../assets/content/novica-paunovski.png" alt="Vue">
            </NuxtLink>
            <span v-if="isExpanded" class="ml-4 font-bold text-lg">Novica Paunovski</span>
          </div>
          <div class="sidebar-toggle-wrapper flex justify-end mb-4">
            <button class="sidebar-toggle hover:text-slate-400 cursor-pointer" @click="toggleSidebar">
              <span class="material-icons">keyboard_double_arrow_right</span>
            </button>
          </div>
      </aside>
      <div id="body">
        <slot />
      </div>
    </main>
</template>

<script setup>
  const isExpanded = ref(false);

  const toggleSidebar = () => {
    isExpanded.value = !isExpanded.value;
  }
</script>

<style scoped>
  .router-link-exact-active {
    color: #12b488;
  }

  #body {
    @media (max-width: 768px) {
      padding-left: 6rem;
    }
  }

  .expanded-width {
    width: 3rem;
  }

  .sidebar-toggle-wrapper {
    position: relative;
    top: 0;
    transition: 0.2s ease-out;
  }

  #sidebar {
    transition: 0.2s ease-out;

    &.is-expanded {
      width: 20%;

      @media (max-width: 768px) {
        width: 50%;
      }

      .logo {
        display: flex;
        justify-content: center;
      }

      

      .sidebar-toggle-wrapper {
        top: -3.6rem;
      }

      .sidebar-toggle {
        transform: rotate(-180deg);
      }
    }

    @media (max-width: 768px) {
      position: fixed;
      z-index: 99;
    }

    width: calc(2.5rem + 32px);
  }
</style>