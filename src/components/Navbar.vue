<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'
import { Bars3Icon, XMarkIcon } from '@heroicons/vue/24/outline'

const isScrolled = ref(false)
const isMobileMenuOpen = ref(false)

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const closeMobileMenu = () => {
  isMobileMenuOpen.value = false
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <nav 
    :class="[
      'fixed top-0 left-0 right-0 z-50 transition-all duration-300',
      isScrolled 
        ? 'glass-effect shadow-lg' 
        : 'bg-white/80 backdrop-blur-md'
    ]"
  >
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between items-center h-16">
        <!-- Logo -->
        <div class="flex-shrink-0">
          <RouterLink 
            to="/" 
            class="flex items-center space-x-2 text-2xl font-bold text-gray-900 hover:text-blue-600 transition-colors duration-300"
            @click="closeMobileMenu"
          >
            <div class="w-8 h-8 bg-gradient-to-br from-blue-600 to-blue-700 rounded-lg flex items-center justify-center">
              <span class="text-white font-bold text-sm">HC</span>
            </div>
            <span class="hidden sm:block">危化品门户</span>
          </RouterLink>
        </div>

        <!-- Desktop Navigation -->
        <div class="hidden md:block">
          <div class="ml-10 flex items-baseline space-x-8">
            <RouterLink
              to="/"
              class="nav-link"
              active-class="nav-link-active"
            >
              首页
            </RouterLink>
            <RouterLink
              to="/products"
              class="nav-link"
              active-class="nav-link-active"
            >
              产品展示
            </RouterLink>
            <RouterLink
              to="/safety"
              class="nav-link"
              active-class="nav-link-active"
            >
              安全信息
            </RouterLink>
            <RouterLink
              to="/about"
              class="nav-link"
              active-class="nav-link-active"
            >
              关于我们
            </RouterLink>
            <RouterLink
              to="/contact"
              class="nav-link"
              active-class="nav-link-active"
            >
              联系我们
            </RouterLink>
          </div>
        </div>

        <!-- CTA Button -->
        <div class="hidden md:block">
          <RouterLink
            to="/contact"
            class="btn-primary text-sm px-6 py-2"
          >
            立即咨询
          </RouterLink>
        </div>

        <!-- Mobile menu button -->
        <div class="md:hidden">
          <button
            @click="toggleMobileMenu"
            class="p-2 rounded-lg text-gray-600 hover:text-blue-600 hover:bg-gray-100 transition-colors duration-300"
          >
            <Bars3Icon v-if="!isMobileMenuOpen" class="h-6 w-6" />
            <XMarkIcon v-else class="h-6 w-6" />
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile Navigation Menu -->
    <Transition
      enter-active-class="transition duration-300 ease-out"
      enter-from-class="transform scale-95 opacity-0"
      enter-to-class="transform scale-100 opacity-100"
      leave-active-class="transition duration-200 ease-in"
      leave-from-class="transform scale-100 opacity-100"
      leave-to-class="transform scale-95 opacity-0"
    >
      <div 
        v-if="isMobileMenuOpen" 
        class="md:hidden bg-white/95 backdrop-blur-md border-t border-gray-200"
      >
        <div class="px-2 pt-2 pb-3 space-y-1 sm:px-3">
          <RouterLink
            to="/"
            class="mobile-nav-link"
            active-class="mobile-nav-link-active"
            @click="closeMobileMenu"
          >
            首页
          </RouterLink>
          <RouterLink
            to="/products"
            class="mobile-nav-link"
            active-class="mobile-nav-link-active"
            @click="closeMobileMenu"
          >
            产品展示
          </RouterLink>
          <RouterLink
            to="/safety"
            class="mobile-nav-link"
            active-class="mobile-nav-link-active"
            @click="closeMobileMenu"
          >
            安全信息
          </RouterLink>
          <RouterLink
            to="/about"
            class="mobile-nav-link"
            active-class="mobile-nav-link-active"
            @click="closeMobileMenu"
          >
            关于我们
          </RouterLink>
          <RouterLink
            to="/contact"
            class="mobile-nav-link"
            active-class="mobile-nav-link-active"
            @click="closeMobileMenu"
          >
            联系我们
          </RouterLink>
          <div class="pt-4">
            <RouterLink
              to="/contact"
              class="btn-primary w-full text-center"
              @click="closeMobileMenu"
            >
              立即咨询
            </RouterLink>
          </div>
        </div>
      </div>
    </Transition>
  </nav>
</template>

<style scoped>
@reference "tailwindcss";

.nav-link {
  @apply text-gray-700 hover:text-blue-600 px-3 py-2 rounded-lg text-sm font-medium transition-all duration-300 relative;
}

.nav-link::after {
  content: '';
  @apply absolute bottom-0 left-1/2 w-0 h-0.5 bg-blue-600 transition-all duration-300;
  transform: translateX(-50%);
}

.nav-link:hover::after {
  @apply w-full;
}

.nav-link-active {
  @apply text-blue-600;
}

.nav-link-active::after {
  @apply w-full;
}

.mobile-nav-link {
  @apply text-gray-700 hover:text-blue-600 hover:bg-gray-50 block px-3 py-2 rounded-lg text-base font-medium transition-colors duration-300;
}

.mobile-nav-link-active {
  @apply text-blue-600 bg-blue-600/10;
}
</style>