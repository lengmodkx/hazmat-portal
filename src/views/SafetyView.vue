<template>
  <div class="min-h-screen bg-gradient-to-br from-gray-50 to-gray-100">
    <!-- Hero Section -->
    <section class="relative py-20 bg-gradient-to-r from-green-600 to-emerald-700 text-white overflow-hidden">
      <div class="absolute inset-0 bg-black opacity-10"></div>
      <div class="container mx-auto px-6 relative z-10">
        <div class="text-center max-w-4xl mx-auto">
          <h1 class="text-5xl md:text-6xl font-bold mb-6 animate-fade-in-up">
            安全信息
          </h1>
          <p class="text-xl md:text-2xl text-green-100 mb-8 animate-fade-in-up animation-delay-200">
            专业的危化品安全管理知识与操作指南
          </p>
        </div>
      </div>
    </section>

    <!-- Safety Guidelines -->
    <section class="py-20">
      <div class="container mx-auto px-6">
        <div class="text-center mb-16">
          <h2 class="section-title">安全操作指南</h2>
          <p class="section-subtitle">遵循专业标准，确保操作安全</p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div
            v-for="guideline in safetyGuidelines"
            :key="guideline.id"
            class="bg-white rounded-2xl p-8 shadow-lg hover:shadow-xl transition-all duration-300 group"
          >
            <div class="flex items-center mb-6">
              <div class="w-12 h-12 bg-green-100 rounded-xl flex items-center justify-center group-hover:bg-green-200 transition-colors">
                <component :is="guideline.icon" class="w-6 h-6 text-green-600" />
              </div>
              <h3 class="text-xl font-bold text-gray-900 ml-4">{{ guideline.title }}</h3>
            </div>
            <p class="text-gray-600 mb-4">{{ guideline.description }}</p>
            <ul class="space-y-2">
              <li v-for="point in guideline.points" :key="point" class="flex items-start space-x-2">
                <CheckIcon class="w-5 h-5 text-green-500 mt-0.5 flex-shrink-0" />
                <span class="text-sm text-gray-600">{{ point }}</span>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- Emergency Procedures -->
    <section class="py-20 bg-white">
      <div class="container mx-auto px-6">
        <div class="text-center mb-16">
          <h2 class="section-title">应急处理程序</h2>
          <p class="section-subtitle">快速响应，有效处理突发情况</p>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
          <div
            v-for="procedure in emergencyProcedures"
            :key="procedure.id"
            class="bg-gradient-to-br from-red-50 to-orange-50 rounded-2xl p-8 border border-red-100"
          >
            <div class="flex items-center mb-6">
              <div class="w-12 h-12 bg-red-100 rounded-xl flex items-center justify-center">
                <component :is="procedure.icon" class="w-6 h-6 text-red-600" />
              </div>
              <h3 class="text-xl font-bold text-gray-900 ml-4">{{ procedure.title }}</h3>
            </div>
            <div class="space-y-4">
              <div v-for="(step, index) in procedure.steps" :key="index" class="flex items-start space-x-4">
                <div class="w-8 h-8 bg-red-600 text-white rounded-full flex items-center justify-center text-sm font-bold flex-shrink-0">
                  {{ index + 1 }}
                </div>
                <div>
                  <h4 class="font-semibold text-gray-900 mb-1">{{ step.title }}</h4>
                  <p class="text-gray-600 text-sm">{{ step.description }}</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Safety Equipment -->
    <section class="py-20">
      <div class="container mx-auto px-6">
        <div class="text-center mb-16">
          <h2 class="section-title">安全防护设备</h2>
          <p class="section-subtitle">专业设备，全面防护</p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div
            v-for="equipment in safetyEquipment"
            :key="equipment.id"
            class="bg-white rounded-2xl p-6 shadow-lg hover:shadow-xl transition-all duration-300 text-center group"
          >
            <div class="w-16 h-16 bg-blue-100 rounded-2xl flex items-center justify-center mx-auto mb-4 group-hover:bg-blue-200 transition-colors">
              <component :is="equipment.icon" class="w-8 h-8 text-blue-600" />
            </div>
            <h3 class="text-lg font-bold text-gray-900 mb-2">{{ equipment.name }}</h3>
            <p class="text-gray-600 text-sm mb-4">{{ equipment.description }}</p>
            <div class="text-xs text-gray-500">
              <span class="font-medium">适用场景:</span> {{ equipment.usage }}
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Training Resources -->
    <section class="py-20 bg-gradient-to-r from-blue-600 to-purple-700 text-white">
      <div class="container mx-auto px-6">
        <div class="text-center mb-16">
          <h2 class="text-4xl font-bold mb-4">培训资源</h2>
          <p class="text-xl text-blue-100">提升安全意识，掌握专业技能</p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div
            v-for="resource in trainingResources"
            :key="resource.id"
            class="bg-white bg-opacity-10 backdrop-blur-lg rounded-2xl p-6 hover:bg-opacity-20 transition-all duration-300"
          >
            <div class="flex items-center mb-4">
              <component :is="resource.icon" class="w-8 h-8 text-white mr-3" />
              <h3 class="text-xl font-bold">{{ resource.title }}</h3>
            </div>
            <p class="text-blue-100 mb-4">{{ resource.description }}</p>
            <ul class="space-y-2 mb-6">
              <li v-for="item in resource.items" :key="item" class="flex items-center space-x-2">
                <CheckIcon class="w-4 h-4 text-green-300" />
                <span class="text-sm text-blue-100">{{ item }}</span>
              </li>
            </ul>
            <button class="w-full bg-white text-blue-600 font-semibold py-3 px-6 rounded-xl hover:bg-blue-50 transition-colors">
              了解更多
            </button>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Emergency -->
    <section class="py-20 bg-red-600 text-white">
      <div class="container mx-auto px-6 text-center">
        <h2 class="text-4xl font-bold mb-6">紧急联系方式</h2>
        <p class="text-xl text-red-100 mb-8">遇到紧急情况，请立即联系</p>
        
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8 max-w-4xl mx-auto">
          <div class="bg-white bg-opacity-10 backdrop-blur-lg rounded-2xl p-6">
            <PhoneIcon class="w-12 h-12 text-white mx-auto mb-4" />
            <h3 class="text-xl font-bold mb-2">应急热线</h3>
            <p class="text-2xl font-bold text-yellow-300">400-999-1234</p>
            <p class="text-red-100 text-sm mt-2">24小时全天候服务</p>
          </div>
          
          <div class="bg-white bg-opacity-10 backdrop-blur-lg rounded-2xl p-6">
            <ExclamationTriangleIcon class="w-12 h-12 text-white mx-auto mb-4" />
            <h3 class="text-xl font-bold mb-2">事故报告</h3>
            <p class="text-2xl font-bold text-yellow-300">400-888-5678</p>
            <p class="text-red-100 text-sm mt-2">专业事故处理团队</p>
          </div>
          
          <div class="bg-white bg-opacity-10 backdrop-blur-lg rounded-2xl p-6">
            <EnvelopeIcon class="w-12 h-12 text-white mx-auto mb-4" />
            <h3 class="text-xl font-bold mb-2">邮件咨询</h3>
            <p class="text-lg font-bold text-yellow-300">safety@hazmat.com</p>
            <p class="text-red-100 text-sm mt-2">专业安全咨询服务</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import { onMounted } from 'vue'
import {
  CheckIcon,
  ShieldCheckIcon,
  ExclamationTriangleIcon,
  FireIcon,
  EyeIcon,
  HandRaisedIcon,
  HeartIcon,
  PhoneIcon,
  EnvelopeIcon,
  BookOpenIcon,
  VideoCameraIcon,
  DocumentTextIcon,
  BeakerIcon,
  WrenchScrewdriverIcon
} from '@heroicons/vue/24/outline'

interface SafetyGuideline {
  id: number
  title: string
  description: string
  icon: any
  points: string[]
}

interface EmergencyProcedure {
  id: number
  title: string
  icon: any
  steps: {
    title: string
    description: string
  }[]
}

interface SafetyEquipment {
  id: number
  name: string
  description: string
  usage: string
  icon: any
}

interface TrainingResource {
  id: number
  title: string
  description: string
  icon: any
  items: string[]
}

const safetyGuidelines: SafetyGuideline[] = [
  {
    id: 1,
    title: '个人防护',
    description: '正确使用个人防护设备是安全操作的基础',
    icon: ShieldCheckIcon,
    points: [
      '佩戴适当的防护眼镜和面罩',
      '穿着防化服和防护手套',
      '使用呼吸防护设备',
      '定期检查防护设备完整性'
    ]
  },
  {
    id: 2,
    title: '储存管理',
    description: '科学的储存方式确保化学品稳定性和安全性',
    icon: BeakerIcon,
    points: [
      '按化学品性质分类储存',
      '保持适当的温度和湿度',
      '定期检查容器密封性',
      '建立完善的标识系统'
    ]
  },
  {
    id: 3,
    title: '操作规范',
    description: '标准化操作流程降低事故风险',
    icon: WrenchScrewdriverIcon,
    points: [
      '严格按照操作手册执行',
      '避免不相容物质混合',
      '控制操作环境条件',
      '记录操作过程和异常情况'
    ]
  },
  {
    id: 4,
    title: '环境监测',
    description: '实时监测确保工作环境安全',
    icon: EyeIcon,
    points: [
      '定期检测空气质量',
      '监控温度和湿度变化',
      '检查通风系统运行状态',
      '建立预警机制'
    ]
  },
  {
    id: 5,
    title: '废料处理',
    description: '正确处理化学废料保护环境',
    icon: HandRaisedIcon,
    points: [
      '分类收集化学废料',
      '使用专用容器储存',
      '委托有资质机构处理',
      '建立废料处理记录'
    ]
  },
  {
    id: 6,
    title: '健康监护',
    description: '定期健康检查保障员工安全',
    icon: HeartIcon,
    points: [
      '定期进行职业健康体检',
      '建立健康档案',
      '及时处理健康异常',
      '提供健康咨询服务'
    ]
  }
]

const emergencyProcedures: EmergencyProcedure[] = [
  {
    id: 1,
    title: '化学品泄漏处理',
    icon: ExclamationTriangleIcon,
    steps: [
      {
        title: '立即报警',
        description: '发现泄漏后立即通知相关人员，启动应急预案'
      },
      {
        title: '人员疏散',
        description: '疏散泄漏区域人员到安全地带，设置警戒线'
      },
      {
        title: '切断污染源',
        description: '在确保安全的前提下，采取措施阻止泄漏扩散'
      },
      {
        title: '清理处置',
        description: '使用适当的吸附材料清理泄漏物，按规定处置'
      }
    ]
  },
  {
    id: 2,
    title: '火灾应急处理',
    icon: FireIcon,
    steps: [
      {
        title: '报警求助',
        description: '立即拨打119火警电话，同时通知内部应急小组'
      },
      {
        title: '人员撤离',
        description: '组织人员有序撤离，确保逃生通道畅通'
      },
      {
        title: '初期扑救',
        description: '在确保安全的情况下，使用适当的灭火器材扑救'
      },
      {
        title: '配合救援',
        description: '配合消防部门开展救援工作，提供必要信息'
      }
    ]
  }
]

const safetyEquipment: SafetyEquipment[] = [
  {
    id: 1,
    name: '防护眼镜',
    description: '保护眼部免受化学飞溅伤害',
    usage: '所有化学操作',
    icon: EyeIcon
  },
  {
    id: 2,
    name: '防化手套',
    description: '防止化学品接触皮肤',
    usage: '直接接触化学品',
    icon: HandRaisedIcon
  },
  {
    id: 3,
    name: '呼吸器',
    description: '过滤有害气体和颗粒物',
    usage: '有毒气体环境',
    icon: ShieldCheckIcon
  },
  {
    id: 4,
    name: '防化服',
    description: '全身防护，隔离化学品',
    usage: '高危险操作',
    icon: ShieldCheckIcon
  }
]

const trainingResources: TrainingResource[] = [
  {
    id: 1,
    title: '在线课程',
    description: '系统性的安全知识学习平台',
    icon: BookOpenIcon,
    items: [
      '化学品安全基础知识',
      '个人防护设备使用',
      '应急处理程序',
      '法规标准解读'
    ]
  },
  {
    id: 2,
    title: '视频教程',
    description: '直观的操作演示和案例分析',
    icon: VideoCameraIcon,
    items: [
      '标准操作流程演示',
      '事故案例分析',
      '设备使用指导',
      '应急演练视频'
    ]
  },
  {
    id: 3,
    title: '技术文档',
    description: '详细的技术资料和操作手册',
    icon: DocumentTextIcon,
    items: [
      '安全数据表(SDS)',
      '操作规程手册',
      '应急预案模板',
      '法规政策文件'
    ]
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
  document.querySelectorAll('.group, .bg-gradient-to-br, .bg-white').forEach((el) => {
    observer.observe(el)
  })
})
</script>

<style scoped>
.animation-delay-200 {
  animation-delay: 200ms;
}
</style>