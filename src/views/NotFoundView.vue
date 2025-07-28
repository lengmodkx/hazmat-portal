<template>
  <div class="min-h-screen bg-gradient-to-br from-gray-50 to-gray-100 flex items-center justify-center">
    <div class="text-center max-w-2xl mx-auto px-6">
      <!-- 404 Animation -->
      <div class="mb-8">
        <div class="relative">
          <h1 class="text-9xl md:text-[12rem] font-bold text-gray-200 select-none animate-pulse">
            404
          </h1>
          <div class="absolute inset-0 flex items-center justify-center">
            <div class="w-32 h-32 bg-gradient-to-br from-blue-500 to-purple-600 rounded-full flex items-center justify-center animate-bounce">
              <ExclamationTriangleIcon class="w-16 h-16 text-white" />
            </div>
          </div>
        </div>
      </div>

      <!-- Error Message -->
      <div class="mb-8">
        <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">
          页面未找到
        </h2>
        <p class="text-lg text-gray-600 mb-6">
          抱歉，您访问的页面不存在或已被移动。
        </p>
        <p class="text-gray-500">
          请检查URL是否正确，或返回首页继续浏览。
        </p>
      </div>

      <!-- Action Buttons -->
      <div class="flex flex-col sm:flex-row gap-4 justify-center mb-12">
        <router-link
          to="/"
          class="btn-primary inline-flex items-center justify-center"
        >
          <HomeIcon class="w-5 h-5 mr-2" />
          返回首页
        </router-link>
        <button
          @click="goBack"
          class="btn-secondary inline-flex items-center justify-center"
        >
          <ArrowLeftIcon class="w-5 h-5 mr-2" />
          返回上页
        </button>
      </div>

      <!-- Quick Links -->
      <div class="bg-white rounded-2xl p-8 shadow-lg">
        <h3 class="text-xl font-bold text-gray-900 mb-6">您可能在寻找</h3>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
          <router-link
            v-for="link in quickLinks"
            :key="link.path"
            :to="link.path"
            class="flex items-center p-4 rounded-xl border border-gray-200 hover:border-blue-300 hover:bg-blue-50 transition-all duration-200 group"
          >
            <div class="w-10 h-10 bg-blue-100 rounded-lg flex items-center justify-center mr-4 group-hover:bg-blue-200 transition-colors">
              <component :is="link.icon" class="w-5 h-5 text-blue-600" />
            </div>
            <div class="text-left">
              <h4 class="font-semibold text-gray-900 group-hover:text-blue-600 transition-colors">
                {{ link.title }}
              </h4>
              <p class="text-sm text-gray-500">{{ link.description }}</p>
            </div>
          </router-link>
        </div>
      </div>

      <!-- Contact Support -->
      <div class="mt-12 p-6 bg-gradient-to-r from-blue-600 to-purple-600 rounded-2xl text-white">
        <h3 class="text-xl font-bold mb-2">需要帮助？</h3>
        <p class="text-blue-100 mb-4">如果您仍然无法找到所需内容，请联系我们的客服团队</p>
        <div class="flex flex-col sm:flex-row gap-3 justify-center">
          <a
            href="tel:400-999-1234"
            class="inline-flex items-center justify-center px-6 py-3 bg-white bg-opacity-20 backdrop-blur-lg rounded-xl hover:bg-opacity-30 transition-all duration-200"
          >
            <PhoneIcon class="w-5 h-5 mr-2" />
            400-999-1234
          </a>
          <router-link
            to="/contact"
            class="inline-flex items-center justify-center px-6 py-3 bg-white bg-opacity-20 backdrop-blur-lg rounded-xl hover:bg-opacity-30 transition-all duration-200"
          >
            <EnvelopeIcon class="w-5 h-5 mr-2" />
            在线咨询
          </router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { useRouter } from 'vue-router'
import {
  ExclamationTriangleIcon,
  HomeIcon,
  ArrowLeftIcon,
  PhoneIcon,
  EnvelopeIcon,
  BeakerIcon,
  ShieldCheckIcon,
  BuildingOfficeIcon,
  ChatBubbleLeftRightIcon
} from '@heroicons/vue/24/outline'

interface QuickLink {
  path: string
  title: string
  description: string
  icon: any
}

const router = useRouter()

const quickLinks: QuickLink[] = [
  {
    path: '/products',
    title: '产品展示',
    description: '查看我们的危化品产品',
    icon: BeakerIcon
  },
  {
    path: '/safety',
    title: '安全信息',
    description: '了解安全操作指南',
    icon: ShieldCheckIcon
  },
  {
    path: '/about',
    title: '关于我们',
    description: '了解公司信息',
    icon: BuildingOfficeIcon
  },
  {
    path: '/contact',
    title: '联系我们',
    description: '获取专业支持',
    icon: ChatBubbleLeftRightIcon
  }
]

const goBack = () => {
  if (window.history.length > 1) {
    router.go(-1)
  } else {
    router.push('/')
  }
}
</script>

<style scoped>
/* 添加一些自定义动画 */
@keyframes float {
  0%, 100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-10px);
  }
}

.animate-float {
  animation: float 3s ease-in-out infinite;
}
</style>