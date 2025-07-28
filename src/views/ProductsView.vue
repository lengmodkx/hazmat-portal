<template>
  <div class="min-h-screen bg-gradient-to-br from-gray-50 to-gray-100">
    <!-- Hero Section -->
    <section class="relative py-20 bg-gradient-to-r from-blue-600 to-blue-800 text-white overflow-hidden">
      <div class="absolute inset-0 bg-black opacity-10"></div>
      <div class="container mx-auto px-6 relative z-10">
        <div class="text-center max-w-4xl mx-auto">
          <h1 class="text-5xl md:text-6xl font-bold mb-6 animate-fade-in-up">
            产品展示
          </h1>
          <p class="text-xl md:text-2xl text-blue-100 mb-8 animate-fade-in-up animation-delay-200">
            专业的危化品管理解决方案
          </p>
        </div>
      </div>
    </section>

    <!-- Filter Section -->
    <section class="py-12">
      <div class="container mx-auto px-6">
        <div class="flex flex-wrap justify-center gap-4 mb-12">
          <button
            v-for="category in categories"
            :key="category.id"
            @click="selectedCategory = category.id"
            :class="[
              'px-6 py-3 rounded-full font-medium transition-all duration-300',
              selectedCategory === category.id
                ? 'bg-blue-600 text-white shadow-lg'
                : 'bg-white text-gray-700 hover:bg-gray-50 shadow-md'
            ]"
          >
            {{ category.name }}
          </button>
        </div>
      </div>
    </section>

    <!-- Products Grid -->
    <section class="pb-20">
      <div class="container mx-auto px-6">
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div
            v-for="product in filteredProducts"
            :key="product.id"
            class="bg-white rounded-2xl shadow-lg hover:shadow-xl transition-all duration-300 overflow-hidden group"
            @click="openProductModal(product)"
          >
            <div class="relative h-48 bg-gradient-to-br from-gray-100 to-gray-200">
              <div class="absolute inset-0 flex items-center justify-center">
                <div class="w-20 h-20 bg-blue-600 rounded-full flex items-center justify-center">
                  <component :is="getHazardIcon(product.hazardLevel)" class="w-10 h-10 text-white" />
                </div>
              </div>
              <div class="absolute top-4 right-4">
                <span
                  :class="[
                    'px-3 py-1 rounded-full text-sm font-medium',
                    getHazardLevelClass(product.hazardLevel)
                  ]"
                >
                  {{ getHazardLevelText(product.hazardLevel) }}
                </span>
              </div>
            </div>
            <div class="p-6">
              <h3 class="text-xl font-bold text-gray-900 mb-2 group-hover:text-blue-600 transition-colors">
                {{ product.name }}
              </h3>
              <p class="text-gray-600 mb-4 line-clamp-2">
                {{ product.description }}
              </p>
              <div class="flex items-center justify-between">
                <span class="text-sm text-gray-500">
                  CAS: {{ product.casNumber }}
                </span>
                <ChevronRightIcon class="w-5 h-5 text-gray-400 group-hover:text-blue-600 transition-colors" />
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Product Modal -->
    <div
      v-if="selectedProduct"
      class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4 z-50"
      @click="closeProductModal"
    >
      <div
        class="bg-white rounded-2xl max-w-2xl w-full max-h-[90vh] overflow-y-auto"
        @click.stop
      >
        <div class="p-6">
          <div class="flex items-center justify-between mb-6">
            <h2 class="text-2xl font-bold text-gray-900">{{ selectedProduct.name }}</h2>
            <button
              @click="closeProductModal"
              class="p-2 hover:bg-gray-100 rounded-full transition-colors"
            >
              <XMarkIcon class="w-6 h-6 text-gray-500" />
            </button>
          </div>
          
          <div class="space-y-6">
            <div class="flex items-center space-x-4">
              <div class="w-16 h-16 bg-blue-600 rounded-full flex items-center justify-center">
                <component :is="getHazardIcon(selectedProduct.hazardLevel)" class="w-8 h-8 text-white" />
              </div>
              <div>
                <span
                  :class="[
                    'px-4 py-2 rounded-full text-sm font-medium',
                    getHazardLevelClass(selectedProduct.hazardLevel)
                  ]"
                >
                  {{ getHazardLevelText(selectedProduct.hazardLevel) }}
                </span>
              </div>
            </div>

            <div>
              <h3 class="text-lg font-semibold text-gray-900 mb-2">基本信息</h3>
              <div class="grid grid-cols-2 gap-4 text-sm">
                <div>
                  <span class="text-gray-500">CAS号:</span>
                  <span class="ml-2 font-medium">{{ selectedProduct.casNumber }}</span>
                </div>
                <div>
                  <span class="text-gray-500">分子式:</span>
                  <span class="ml-2 font-medium">{{ selectedProduct.formula }}</span>
                </div>
                <div>
                  <span class="text-gray-500">分子量:</span>
                  <span class="ml-2 font-medium">{{ selectedProduct.molecularWeight }}</span>
                </div>
                <div>
                  <span class="text-gray-500">沸点:</span>
                  <span class="ml-2 font-medium">{{ selectedProduct.boilingPoint }}</span>
                </div>
              </div>
            </div>

            <div>
              <h3 class="text-lg font-semibold text-gray-900 mb-2">产品描述</h3>
              <p class="text-gray-600">{{ selectedProduct.description }}</p>
            </div>

            <div>
              <h3 class="text-lg font-semibold text-gray-900 mb-2">安全信息</h3>
              <div class="space-y-2">
                <div v-for="safety in selectedProduct.safetyInfo" :key="safety" class="flex items-start space-x-2">
                  <ExclamationTriangleIcon class="w-5 h-5 text-yellow-500 mt-0.5 flex-shrink-0" />
                  <span class="text-sm text-gray-600">{{ safety }}</span>
                </div>
              </div>
            </div>

            <div>
              <h3 class="text-lg font-semibold text-gray-900 mb-2">储存要求</h3>
              <div class="space-y-2">
                <div v-for="storage in selectedProduct.storageRequirements" :key="storage" class="flex items-start space-x-2">
                  <ShieldCheckIcon class="w-5 h-5 text-green-500 mt-0.5 flex-shrink-0" />
                  <span class="text-sm text-gray-600">{{ storage }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, onMounted } from 'vue'
import {
  ChevronRightIcon,
  XMarkIcon,
  ExclamationTriangleIcon,
  ShieldCheckIcon,
  FireIcon,
  BeakerIcon,
  BoltIcon
} from '@heroicons/vue/24/outline'

interface Product {
  id: number
  name: string
  description: string
  casNumber: string
  formula: string
  molecularWeight: string
  boilingPoint: string
  hazardLevel: 'low' | 'medium' | 'high'
  category: string
  safetyInfo: string[]
  storageRequirements: string[]
}

interface Category {
  id: string
  name: string
}

const selectedCategory = ref('all')
const selectedProduct = ref<Product | null>(null)

const categories: Category[] = [
  { id: 'all', name: '全部' },
  { id: 'acids', name: '酸类' },
  { id: 'bases', name: '碱类' },
  { id: 'solvents', name: '溶剂' },
  { id: 'oxidizers', name: '氧化剂' },
  { id: 'flammable', name: '易燃品' }
]

const products: Product[] = [
  {
    id: 1,
    name: '浓硫酸',
    description: '强酸性腐蚀性液体，广泛用于化学工业中的各种反应和制备过程。',
    casNumber: '7664-93-9',
    formula: 'H₂SO₄',
    molecularWeight: '98.08 g/mol',
    boilingPoint: '337°C',
    hazardLevel: 'high',
    category: 'acids',
    safetyInfo: [
      '强腐蚀性，接触皮肤会造成严重烧伤',
      '与水混合时会产生大量热量，可能导致飞溅',
      '吸入蒸气会损伤呼吸道',
      '与有机物接触可能引起燃烧或爆炸'
    ],
    storageRequirements: [
      '储存在阴凉、干燥、通风良好的地方',
      '远离热源、火源和氧化剂',
      '使用耐腐蚀的容器',
      '避免与碱性物质接触'
    ]
  },
  {
    id: 2,
    name: '氢氧化钠',
    description: '强碱性化学品，俗称烧碱或苛性钠，是重要的化工原料。',
    casNumber: '1310-73-2',
    formula: 'NaOH',
    molecularWeight: '40.00 g/mol',
    boilingPoint: '1388°C',
    hazardLevel: 'high',
    category: 'bases',
    safetyInfo: [
      '强腐蚀性，对皮肤、眼睛有严重损害',
      '吸入粉尘会刺激呼吸道',
      '与酸类物质反应剧烈',
      '遇水放热，可能导致飞溅'
    ],
    storageRequirements: [
      '密封保存，防止吸湿',
      '远离酸类和有机物',
      '储存在干燥通风处',
      '使用防腐蚀包装'
    ]
  },
  {
    id: 3,
    name: '丙酮',
    description: '无色透明液体，具有特殊的辛辣气味，是重要的有机溶剂。',
    casNumber: '67-64-1',
    formula: 'C₃H₆O',
    molecularWeight: '58.08 g/mol',
    boilingPoint: '56.5°C',
    hazardLevel: 'medium',
    category: 'solvents',
    safetyInfo: [
      '易燃液体，闪点低',
      '蒸气与空气形成爆炸性混合物',
      '对眼睛和呼吸道有刺激性',
      '长期接触可能影响神经系统'
    ],
    storageRequirements: [
      '储存在阴凉通风处',
      '远离火源、热源和氧化剂',
      '容器必须密封',
      '防止静电积累'
    ]
  },
  {
    id: 4,
    name: '过氧化氢',
    description: '强氧化剂，常用作漂白剂、消毒剂和化学反应的氧化剂。',
    casNumber: '7722-84-1',
    formula: 'H₂O₂',
    molecularWeight: '34.01 g/mol',
    boilingPoint: '150.2°C',
    hazardLevel: 'medium',
    category: 'oxidizers',
    safetyInfo: [
      '强氧化性，与可燃物接触可能引起燃烧',
      '浓溶液对皮肤有腐蚀性',
      '分解时产生氧气，可能导致容器破裂',
      '与重金属离子接触会加速分解'
    ],
    storageRequirements: [
      '储存在阴凉避光处',
      '使用专用容器，避免金属污染',
      '远离可燃物和还原剂',
      '定期检查容器完整性'
    ]
  },
  {
    id: 5,
    name: '乙醇',
    description: '无色透明液体，具有特殊香味，是常用的有机溶剂和燃料。',
    casNumber: '64-17-5',
    formula: 'C₂H₆O',
    molecularWeight: '46.07 g/mol',
    boilingPoint: '78.4°C',
    hazardLevel: 'low',
    category: 'flammable',
    safetyInfo: [
      '易燃液体，蒸气易燃',
      '大量摄入对人体有害',
      '蒸气可能引起头晕',
      '与强氧化剂反应剧烈'
    ],
    storageRequirements: [
      '储存在阴凉通风处',
      '远离火源和热源',
      '容器密封良好',
      '避免阳光直射'
    ]
  },
  {
    id: 6,
    name: '甲苯',
    description: '无色透明液体，具有苯样气味，是重要的化工原料和溶剂。',
    casNumber: '108-88-3',
    formula: 'C₇H₈',
    molecularWeight: '92.14 g/mol',
    boilingPoint: '110.6°C',
    hazardLevel: 'medium',
    category: 'solvents',
    safetyInfo: [
      '易燃液体，蒸气有毒',
      '长期接触可能影响神经系统',
      '对皮肤有刺激性',
      '蒸气浓度过高可能导致窒息'
    ],
    storageRequirements: [
      '储存在阴凉通风的专用库房',
      '远离火源、热源和氧化剂',
      '使用防爆电器设备',
      '定期检测蒸气浓度'
    ]
  }
]

const filteredProducts = computed(() => {
  if (selectedCategory.value === 'all') {
    return products
  }
  return products.filter(product => product.category === selectedCategory.value)
})

const getHazardIcon = (level: string) => {
  switch (level) {
    case 'high':
      return FireIcon
    case 'medium':
      return ExclamationTriangleIcon
    case 'low':
      return ShieldCheckIcon
    default:
      return BeakerIcon
  }
}

const getHazardLevelClass = (level: string) => {
  switch (level) {
    case 'high':
      return 'bg-red-100 text-red-800'
    case 'medium':
      return 'bg-yellow-100 text-yellow-800'
    case 'low':
      return 'bg-green-100 text-green-800'
    default:
      return 'bg-gray-100 text-gray-800'
  }
}

const getHazardLevelText = (level: string) => {
  switch (level) {
    case 'high':
      return '高危险'
    case 'medium':
      return '中危险'
    case 'low':
      return '低危险'
    default:
      return '未知'
  }
}

const openProductModal = (product: Product) => {
  selectedProduct.value = product
  document.body.style.overflow = 'hidden'
}

const closeProductModal = () => {
  selectedProduct.value = null
  document.body.style.overflow = 'auto'
}

onMounted(() => {
  // 添加滚动动画
  const observerOptions = {
    threshold: 0.1,
    rootMargin: '0px 0px -50px 0px'
  }

  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        entry.target.classList.add('animate-fade-in-up')
      }
    })
  }, observerOptions)

  // 观察所有产品卡片
  document.querySelectorAll('.group').forEach((el) => {
    observer.observe(el)
  })
})
</script>

<style scoped>
.line-clamp-2 {
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.animation-delay-200 {
  animation-delay: 200ms;
}
</style>