<template>
  <div class="min-h-screen bg-gradient-to-br from-gray-50 to-gray-100">
    <!-- Hero Section -->
    <section class="relative py-20 bg-gradient-to-r from-purple-600 to-indigo-700 text-white overflow-hidden">
      <div class="absolute inset-0 bg-black opacity-10"></div>
      <div class="container mx-auto px-6 relative z-10">
        <div class="text-center max-w-4xl mx-auto">
          <h1 class="text-5xl md:text-6xl font-bold mb-6 animate-fade-in-up">
            关于我们
          </h1>
          <p class="text-xl md:text-2xl text-purple-100 mb-8 animate-fade-in-up animation-delay-200">
            专业的危化品管理解决方案提供商
          </p>
        </div>
      </div>
    </section>

    <!-- Company Introduction -->
    <section class="py-20">
      <div class="container mx-auto px-6">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 items-center">
          <div>
            <h2 class="text-4xl font-bold text-gray-900 mb-6">我们的使命</h2>
            <p class="text-lg text-gray-600 mb-6 leading-relaxed">
              致力于为全球企业提供最安全、最可靠的危化品管理解决方案。我们相信，通过先进的技术和专业的服务，
              可以让危化品的使用变得更加安全、高效和环保。
            </p>
            <p class="text-lg text-gray-600 mb-8 leading-relaxed">
              自成立以来，我们始终坚持以客户为中心，以安全为核心，不断创新和完善我们的产品和服务，
              为客户创造更大的价值，为社会的可持续发展贡献力量。
            </p>
            <div class="grid grid-cols-2 gap-6">
              <div class="text-center">
                <div class="text-3xl font-bold text-purple-600 mb-2">15+</div>
                <div class="text-gray-600">年行业经验</div>
              </div>
              <div class="text-center">
                <div class="text-3xl font-bold text-purple-600 mb-2">500+</div>
                <div class="text-gray-600">合作客户</div>
              </div>
            </div>
          </div>
          <div class="relative">
            <div class="bg-gradient-to-br from-purple-100 to-indigo-100 rounded-2xl p-8 h-96 flex items-center justify-center">
              <div class="text-center">
                <BuildingOfficeIcon class="w-24 h-24 text-purple-600 mx-auto mb-4" />
                <h3 class="text-2xl font-bold text-gray-900 mb-2">专业团队</h3>
                <p class="text-gray-600">汇聚行业精英，提供专业服务</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Core Values -->
    <section class="py-20 bg-white">
      <div class="container mx-auto px-6">
        <div class="text-center mb-16">
          <h2 class="section-title">核心价值观</h2>
          <p class="section-subtitle">指导我们前进的核心理念</p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div
            v-for="value in coreValues"
            :key="value.id"
            class="text-center group"
          >
            <div class="w-20 h-20 bg-gradient-to-br from-purple-100 to-indigo-100 rounded-2xl flex items-center justify-center mx-auto mb-6 group-hover:from-purple-200 group-hover:to-indigo-200 transition-all duration-300">
              <component :is="value.icon" class="w-10 h-10 text-purple-600" />
            </div>
            <h3 class="text-xl font-bold text-gray-900 mb-3">{{ value.title }}</h3>
            <p class="text-gray-600">{{ value.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Team Section -->
    <section class="py-20">
      <div class="container mx-auto px-6">
        <div class="text-center mb-16">
          <h2 class="section-title">核心团队</h2>
          <p class="section-subtitle">经验丰富的专业团队</p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div
            v-for="member in teamMembers"
            :key="member.id"
            class="bg-white rounded-2xl p-8 shadow-lg hover:shadow-xl transition-all duration-300 text-center group"
          >
            <div class="w-24 h-24 bg-gradient-to-br from-gray-200 to-gray-300 rounded-full mx-auto mb-6 flex items-center justify-center group-hover:from-purple-100 group-hover:to-indigo-100 transition-all duration-300">
              <UserIcon class="w-12 h-12 text-gray-600 group-hover:text-purple-600 transition-colors" />
            </div>
            <h3 class="text-xl font-bold text-gray-900 mb-2">{{ member.name }}</h3>
            <p class="text-purple-600 font-medium mb-3">{{ member.position }}</p>
            <p class="text-gray-600 text-sm mb-4">{{ member.description }}</p>
            <div class="flex flex-wrap gap-2 justify-center">
              <span
                v-for="skill in member.skills"
                :key="skill"
                class="px-3 py-1 bg-purple-100 text-purple-700 rounded-full text-xs font-medium"
              >
                {{ skill }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Company Timeline -->
    <section class="py-20 bg-gradient-to-r from-purple-600 to-indigo-700 text-white">
      <div class="container mx-auto px-6">
        <div class="text-center mb-16">
          <h2 class="text-4xl font-bold mb-4">发展历程</h2>
          <p class="text-xl text-purple-100">见证我们的成长足迹</p>
        </div>

        <div class="max-w-4xl mx-auto">
          <div class="space-y-8">
            <div
              v-for="(milestone, index) in milestones"
              :key="milestone.id"
              class="flex items-center space-x-6"
            >
              <div class="flex-shrink-0">
                <div class="w-16 h-16 bg-white bg-opacity-20 backdrop-blur-lg rounded-full flex items-center justify-center">
                  <span class="text-2xl font-bold">{{ index + 1 }}</span>
                </div>
              </div>
              <div class="flex-1 bg-white bg-opacity-10 backdrop-blur-lg rounded-2xl p-6">
                <div class="flex items-center justify-between mb-3">
                  <h3 class="text-xl font-bold">{{ milestone.title }}</h3>
                  <span class="text-purple-200 font-medium">{{ milestone.year }}</span>
                </div>
                <p class="text-purple-100">{{ milestone.description }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Certifications -->
    <section class="py-20 bg-white">
      <div class="container mx-auto px-6">
        <div class="text-center mb-16">
          <h2 class="section-title">资质认证</h2>
          <p class="section-subtitle">权威认证，品质保证</p>
        </div>

        <div class="grid grid-cols-2 md:grid-cols-4 gap-8">
          <div
            v-for="cert in certifications"
            :key="cert.id"
            class="text-center group"
          >
            <div class="w-20 h-20 bg-gradient-to-br from-blue-100 to-purple-100 rounded-2xl flex items-center justify-center mx-auto mb-4 group-hover:from-blue-200 group-hover:to-purple-200 transition-all duration-300">
              <component :is="cert.icon" class="w-10 h-10 text-blue-600" />
            </div>
            <h3 class="text-lg font-bold text-gray-900 mb-2">{{ cert.name }}</h3>
            <p class="text-gray-600 text-sm">{{ cert.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact CTA -->
    <section class="py-20 bg-gradient-to-r from-gray-900 to-gray-800 text-white">
      <div class="container mx-auto px-6 text-center">
        <h2 class="text-4xl font-bold mb-6">与我们合作</h2>
        <p class="text-xl text-gray-300 mb-8 max-w-2xl mx-auto">
          选择我们，选择专业与安全。让我们携手共创更安全的化工未来。
        </p>
        <div class="flex flex-col sm:flex-row gap-4 justify-center">
          <router-link
            to="/contact"
            class="btn-primary inline-flex items-center justify-center"
          >
            <PhoneIcon class="w-5 h-5 mr-2" />
            联系我们
          </router-link>
          <router-link
            to="/products"
            class="btn-secondary inline-flex items-center justify-center"
          >
            <EyeIcon class="w-5 h-5 mr-2" />
            查看产品
          </router-link>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import { onMounted } from 'vue'
import {
  BuildingOfficeIcon,
  UserIcon,
  PhoneIcon,
  EyeIcon,
  ShieldCheckIcon,
  LightBulbIcon,
  HeartIcon,
  StarIcon,
  AcademicCapIcon,
  CheckBadgeIcon,
  GlobeAltIcon,
  CogIcon
} from '@heroicons/vue/24/outline'

interface CoreValue {
  id: number
  title: string
  description: string
  icon: any
}

interface TeamMember {
  id: number
  name: string
  position: string
  description: string
  skills: string[]
}

interface Milestone {
  id: number
  year: string
  title: string
  description: string
}

interface Certification {
  id: number
  name: string
  description: string
  icon: any
}

const coreValues: CoreValue[] = [
  {
    id: 1,
    title: '安全第一',
    description: '将安全放在首位，确保每一个操作都符合最高安全标准',
    icon: ShieldCheckIcon
  },
  {
    id: 2,
    title: '持续创新',
    description: '不断探索新技术，为客户提供更优质的解决方案',
    icon: LightBulbIcon
  },
  {
    id: 3,
    title: '客户至上',
    description: '以客户需求为导向，提供个性化的专业服务',
    icon: HeartIcon
  },
  {
    id: 4,
    title: '追求卓越',
    description: '精益求精，在每个细节上都力求完美',
    icon: StarIcon
  }
]

const teamMembers: TeamMember[] = [
  {
    id: 1,
    name: '张明华',
    position: '首席执行官',
    description: '拥有20年化工行业经验，致力于推动危化品管理技术创新',
    skills: ['战略规划', '行业洞察', '团队领导']
  },
  {
    id: 2,
    name: '李晓雯',
    position: '技术总监',
    description: '化学工程博士，专注于危化品安全技术研发和应用',
    skills: ['技术研发', '安全评估', '产品设计']
  },
  {
    id: 3,
    name: '王建国',
    position: '安全总监',
    description: '注册安全工程师，负责公司安全管理体系建设',
    skills: ['安全管理', '风险评估', '应急响应']
  },
  {
    id: 4,
    name: '陈美玲',
    position: '市场总监',
    description: '市场营销专家，深耕化工行业市场多年',
    skills: ['市场分析', '客户关系', '品牌推广']
  },
  {
    id: 5,
    name: '刘志强',
    position: '运营总监',
    description: '运营管理专家，优化业务流程，提升服务效率',
    skills: ['运营管理', '流程优化', '质量控制']
  },
  {
    id: 6,
    name: '赵丽娜',
    position: '研发经理',
    description: '化学分析专家，负责新产品研发和技术创新',
    skills: ['产品研发', '技术创新', '质量检测']
  }
]

const milestones: Milestone[] = [
  {
    id: 1,
    year: '2008',
    title: '公司成立',
    description: '在上海成立，专注于危化品管理解决方案'
  },
  {
    id: 2,
    year: '2012',
    title: '技术突破',
    description: '自主研发的危化品监测系统获得国家专利'
  },
  {
    id: 3,
    year: '2016',
    title: '市场扩张',
    description: '业务覆盖全国主要工业城市，客户超过200家'
  },
  {
    id: 4,
    year: '2020',
    title: '数字化转型',
    description: '推出智能化危化品管理平台，实现全流程数字化'
  },
  {
    id: 5,
    year: '2023',
    title: '国际合作',
    description: '与多家国际知名企业建立战略合作关系'
  }
]

const certifications: Certification[] = [
  {
    id: 1,
    name: 'ISO 9001',
    description: '质量管理体系认证',
    icon: CheckBadgeIcon
  },
  {
    id: 2,
    name: 'ISO 14001',
    description: '环境管理体系认证',
    icon: GlobeAltIcon
  },
  {
    id: 3,
    name: 'OHSAS 18001',
    description: '职业健康安全管理体系',
    icon: ShieldCheckIcon
  },
  {
    id: 4,
    name: '高新技术企业',
    description: '国家高新技术企业认定',
    icon: AcademicCapIcon
  }
]

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

  // 观察所有需要动画的元素
  document.querySelectorAll('.group, .bg-white, .bg-gradient-to-br').forEach((el) => {
    observer.observe(el)
  })
})
</script>

<style scoped>
.animation-delay-200 {
  animation-delay: 200ms;
}
</style>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
