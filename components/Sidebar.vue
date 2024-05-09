<template>
    <aside id="sidebar" :class="`${isExpanded ? 'is-expanded' : 'items-center'} sidebar flex flex-col min-h-screen bg-slate-800 text-slate-200 overflow-hidden p-4`">
        <div class="logo mb-4 mt-2 flex flex-row justify-between items-center px-1">
            <img  class="w-12" src="../assets/content/novica-paunovski.png" alt="Vue">
            <span v-if="isExpanded" class="ml-4 font-bold text-lg mr-2 flex flex-col justify-start">Novica <span>Paunovski</span></span>
            <button v-if="isExpanded" class="hover:text-slate-400 cursor-pointer ml-4" @click="toggleSidebar">
              <span class="material-icons">keyboard_double_arrow_left</span>
            </button>
        </div>
          <div class="sidebar-toggle-wrapper flex justify-end mb-4" v-if="!isExpanded">
            <button class="sidebar-toggle hover:text-slate-400 cursor-pointer" @click="toggleSidebar">
              <span class="material-icons">keyboard_double_arrow_right</span>
            </button>
          </div>
          <div class="menu-wrapper mb-4 w-full border-t border-slate-400">
            <div :class="`${isExpanded ? 'ml-6' : 'ml-3'}`">
              <UTooltip text="Home" class="flex mt-8">
                <NuxtLink class="flex flex-row justify-start items-center cursor-pointer" to="/">
                    <span class="material-icons">home</span>
                    <span v-if="isExpanded" class="font-bold text-lg ml-4">Home</span>
                </NuxtLink>
              </UTooltip>
              <UTooltip text="Skills" class="flex mt-8">
                <NuxtLink class="flex flex-row justify-start items-center cursor-pointer" to="skills">
                    <span class="material-icons">account_circle</span>
                    <span v-if="isExpanded" class="font-bold text-lg ml-4">Experience</span>
                </NuxtLink>
              </UTooltip>
              <UTooltip text="Hobbies" class="flex mt-8">
                <NuxtLink class="flex flex-row justify-start items-center cursor-pointer" to="hobbies">
                    <span class="material-icons">sports_esports</span>
                    <span v-if="isExpanded" class="font-bold text-lg ml-4">Hobbies</span>
                </NuxtLink>
              </UTooltip>
              <UTooltip text="Contact" class="flex mt-8">
                <NuxtLink class="flex flex-row justify-start items-center cursor-pointer" to="contact">
                    <img v-if="!(currentRoute.name == 'contact')" src="../assets/content/icons8-discord-24.svg" class="w-6 h-6"/>
                    <img v-if="(currentRoute.name == 'contact')" src="../assets/content/discord-mark-slate.svg" class="w-6 h-6"/>
                    <span v-if="isExpanded" class="font-bold text-lg ml-4">Contact</span>
                </NuxtLink>
              </UTooltip>
              <UTooltip text="GitHub">
                <a class="flex flex-row justify-start items-center mt-8 cursor-pointer" href="https://github.com/NovicaPaunovski" target="_blank">
                    <img src="../assets/content/github-mark-white.svg" class="w-6 h-6"/>
                    <span v-if="isExpanded" class="font-bold text-lg ml-4">GitHub</span>
                </a>
              </UTooltip>
            </div>
          </div>
      </aside>
</template>

<script setup lang="ts">
  const isExpanded = ref(false);

  const { currentRoute } = useRouter();

  const toggleSidebar = () => {
    isExpanded.value = !isExpanded.value;
  }
</script>

<style scoped>
.router-link-exact-active {
    color: rgb(148 163 184);
  }

  #sidebar {
    transition: 0.2s ease-out;

    &.is-expanded {
      width: 25%;

      @media (min-width: 1366px) {
        width: 15%;
      }

      @media (max-width: 768px) {
        width: 60%;
      }

      .logo {
        display: flex;
        justify-content: center;
      }
    }

    @media (max-width: 768px) {
      position: fixed;
      z-index: 99;
    }

    width: calc(3rem + 32px);
  }
</style>