<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { ChevronRightIcon, ShieldCheckIcon, BeakerIcon, DocumentTextIcon, UserGroupIcon } from '@heroicons/vue/24/outline'
import { PlayIcon } from '@heroicons/vue/24/solid'



const observeElements = () => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible')
        }
      })
    },
    { threshold: 0.1 }
  )

  // 查找所有带有animate-on-scroll类的元素
  const elements = document.querySelectorAll('.animate-on-scroll')
  elements.forEach((el) => {
    observer.observe(el)
  })
}

onMounted(() => {
  setTimeout(observeElements, 100)
})

const features = [
  {
    icon: ShieldCheckIcon,
    title: '安全管理',
    description: '全面的安全管理体系，确保危化品储存、运输、使用全过程安全可控。'
  },
  {
    icon: BeakerIcon,
    title: '产品追溯',
    description: '完整的产品生命周期追溯系统，从生产到处置全程可追踪。'
  },
  {
    icon: DocumentTextIcon,
    title: '合规管理',
    description: '实时更新的法规数据库，确保企业运营符合最新安全法规要求。'
  },
  {
    icon: UserGroupIcon,
    title: '专业服务',
    description: '专业的技术团队提供7x24小时技术支持和应急响应服务。'
  }
]

const products = [
  {
    name: '工业溶剂',
    category: '有机化学品',
    hazardLevel: 2,
    description: '高纯度工业溶剂，广泛应用于化工、制药、电子等行业。',
    image: '🧪'
  },
  {
    name: '腐蚀性酸类',
    category: '无机化学品', 
    hazardLevel: 1,
    description: '强腐蚀性酸类产品，需要专业储存和运输条件。',
    image: '⚗️'
  },
  {
    name: '易燃液体',
    category: '危险化学品',
    hazardLevel: 2,
    description: '低闪点易燃液体，严格按照安全规范进行管理。',
    image: '🔥'
  },
  {
    name: '氧化剂',
    category: '特殊化学品',
    hazardLevel: 3,
    description: '强氧化性化学品，需要隔离储存，避免与还原性物质接触。',
    image: '💨'
  }
]

const stats = [
  { number: '500+', label: '合作企业' },
  { number: '1000+', label: '化学品种类' },
  { number: '99.9%', label: '安全记录' },
  { number: '24/7', label: '技术支持' }
]
</script>

<template>
  <div class="overflow-hidden">
    <!-- Hero Section -->
    <section class="relative min-h-screen flex items-center justify-center bg-gradient-to-br from-gray-50 via-white to-gray-100">
      <!-- 背景装饰 -->
      <div class="absolute inset-0 overflow-hidden">
        <div class="absolute -top-40 -right-40 w-80 h-80 bg-blue-600/10 rounded-full blur-3xl animate-pulse-slow"></div>
        <div class="absolute -bottom-40 -left-40 w-80 h-80 bg-blue-500/10 rounded-full blur-3xl animate-pulse-slow" style="animation-delay: 2s;"></div>
      </div>
      
      <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-20">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
          <!-- 左侧内容 -->
          <div class="text-center lg:text-left">
            <h1 class="text-5xl md:text-6xl lg:text-7xl font-bold text-gray-900 mb-6 leading-tight">
              <span class="text-gradient">安全</span>管理<br>
              危化品门户
            </h1>
            <p class="text-xl md:text-2xl text-gray-600 mb-8 leading-relaxed">
              专业的危险化学品管理平台，为企业提供全方位的安全解决方案，确保合规运营。
            </p>
            <div class="flex flex-col sm:flex-row gap-4 justify-center lg:justify-start">
              <RouterLink to="/products" class="btn-primary group">
                探索产品
                <ChevronRightIcon class="ml-2 w-5 h-5 group-hover:translate-x-1 transition-transform duration-300" />
              </RouterLink>
              <button class="btn-secondary group">
                <PlayIcon class="mr-2 w-5 h-5" />
                观看演示
              </button>
            </div>
          </div>
          
          <!-- 右侧动画区域 -->
          <div class="relative h-96 lg:h-[500px]">
            <div class="absolute inset-0 flex items-center justify-center">
              <!-- 浮动元素 -->
              <div class="relative w-full h-full">
                <div class="absolute top-1/4 left-1/4 text-6xl animate-float">
                  🧪
                </div>
                <div class="absolute top-1/2 right-1/4 text-6xl animate-float" style="animation-delay: 2s;">
                  ⚗️
                </div>
                <div class="absolute bottom-1/4 left-1/2 transform -translate-x-1/2 text-6xl animate-float" style="animation-delay: 4s;">
                  🔬
                </div>
                <div class="absolute top-1/3 right-1/3 text-4xl animate-float" style="animation-delay: 1s;">
                  ⚠️
                </div>
                <div class="absolute bottom-1/3 left-1/3 text-4xl animate-float" style="animation-delay: 3s;">
                  🛡️
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 统计数据 -->
    <section class="py-16 bg-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-2 md:grid-cols-4 gap-8">
          <div 
            v-for="(stat, index) in stats" 
            :key="index"
            class="text-center animate-on-scroll"
          >
            <div class="text-4xl md:text-5xl font-bold text-blue-600 mb-2">{{ stat.number }}</div>
            <div class="text-gray-600 font-medium">{{ stat.label }}</div>
          </div>
        </div>
      </div>
    </section>

    <!-- 核心特性 -->
    <section class="py-20 bg-gradient-to-br from-gray-50 to-gray-100">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="section-title animate-on-scroll">
            为什么选择我们
          </h2>
          <p class="section-subtitle animate-on-scroll">
            我们提供业界领先的危化品管理解决方案，帮助企业实现安全、合规、高效的运营管理。
          </p>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div 
            v-for="(feature, index) in features" 
            :key="index"
            class="card p-8 text-center group animate-on-scroll"
          >
            <div class="w-16 h-16 bg-blue-600/10 rounded-2xl flex items-center justify-center mx-auto mb-6 group-hover:bg-blue-600/20 transition-colors duration-300">
              <component :is="feature.icon" class="w-8 h-8 text-blue-600" />
            </div>
            <h3 class="text-xl font-semibold text-gray-900 mb-4">{{ feature.title }}</h3>
            <p class="text-gray-600 leading-relaxed">{{ feature.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- 产品展示 -->
    <section class="py-20 bg-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="section-title animate-on-scroll">
            热门产品
          </h2>
          <p class="section-subtitle animate-on-scroll">
            我们提供多种类型的危险化学品，严格按照国际标准进行分类和管理。
          </p>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div 
            v-for="(product, index) in products" 
            :key="index"
            class="card overflow-hidden group cursor-pointer animate-on-scroll"
          >
            <div class="p-8">
              <div class="text-6xl mb-6 text-center group-hover:scale-110 transition-transform duration-300">
                {{ product.image }}
              </div>
              <div class="mb-4">
                <span 
                  :class="[
                    'inline-block px-3 py-1 rounded-full text-xs font-medium',
                    product.hazardLevel === 1 ? 'hazard-level-1' :
                    product.hazardLevel === 2 ? 'hazard-level-2' :
                    product.hazardLevel === 3 ? 'hazard-level-3' : 'hazard-level-4'
                  ]"
                >
                  危险等级 {{ product.hazardLevel }}
                </span>
              </div>
              <h3 class="text-xl font-semibold text-gray-900 mb-2">{{ product.name }}</h3>
              <p class="text-blue-600 text-sm font-medium mb-3">{{ product.category }}</p>
              <p class="text-gray-600 text-sm leading-relaxed">{{ product.description }}</p>
            </div>
          </div>
        </div>
        
        <div class="text-center mt-12">
          <RouterLink to="/products" class="btn-primary">
            查看全部产品
            <ChevronRightIcon class="ml-2 w-5 h-5" />
          </RouterLink>
        </div>
      </div>
    </section>

    <!-- CTA Section -->
    <section class="py-20 bg-gray-900 text-white relative overflow-hidden">
      <!-- 背景装饰 -->
      <div class="absolute inset-0">
        <div class="absolute top-0 left-0 w-full h-full bg-gradient-to-r from-blue-600/20 to-transparent"></div>
      </div>
      
      <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <h2 class="text-4xl md:text-5xl font-bold mb-6 animate-on-scroll">
          准备开始了吗？
        </h2>
        <p class="text-xl text-gray-300 mb-8 max-w-3xl mx-auto animate-on-scroll">
          联系我们的专业团队，获取定制化的危化品管理解决方案，让您的企业运营更加安全高效。
        </p>
        <div class="flex flex-col sm:flex-row gap-4 justify-center animate-on-scroll">
          <RouterLink to="/contact" class="btn-primary bg-white text-gray-900 hover:bg-gray-100">
            立即咨询
          </RouterLink>
          <RouterLink to="/about" class="btn-secondary border-white text-white hover:bg-white hover:text-gray-900">
            了解更多
          </RouterLink>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
/* 动画样式已在全局CSS中定义 */
</style>