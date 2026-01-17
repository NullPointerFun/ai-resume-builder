<template>
  <div
    :class="[
      'min-h-screen bg-gradient-to-br from-slate-950 via-slate-900 to-slate-950 text-slate-100 flex items-center justify-center px-4 py-10 md:px-8',
      themeClass,
      fontClass
    ]"
  >
    <main
      class="w-full max-w-5xl space-y-6 print-page"
      :class="mainTextSizeClass"
    >
      <section
        class="relative overflow-hidden rounded-3xl px-6 py-7 md:px-10 md:py-9 backdrop-blur-2xl bg-slate-900/70 border"
        :class="heroBorderClass"
      >
        <div
          class="pointer-events-none absolute -top-32 right-0 h-64 w-64 rounded-full bg-emerald-500/10 blur-3xl"
        />
        <div
          class="pointer-events-none absolute -bottom-40 left-10 h-72 w-72 rounded-full bg-cyan-500/10 blur-3xl"
        />
        <div class="relative flex flex-col gap-6 md:flex-row md:items-center">
          <div class="flex-1 space-y-4">
            <div class="flex items-center gap-4">
              <div
                class="h-16 w-16 rounded-full border overflow-hidden bg-slate-900/80 flex items-center justify-center text-[11px] text-slate-500"
                :class="heroAccentBorderClass"
              >
                <img
                  v-if="state.avatarDataUrl"
                  :src="state.avatarDataUrl"
                  alt="avatar"
                  class="h-full w-full object-cover"
                />
                <span v-else>
                  Avatar
                </span>
              </div>
              <div class="space-y-2">
                <div
                  class="inline-flex items-center gap-2 rounded-full border px-3 py-1 text-xs font-mono uppercase tracking-[0.25em]"
                  :class="heroBadgeClass"
                >
                  <span class="h-1.5 w-1.5 rounded-full bg-emerald-400" />
                  <span>AI Engineer Oriented Frontend Intern</span>
                </div>
                <h1
                  class="text-3xl md:text-4xl lg:text-5xl font-semibold tracking-tight"
                >
                  尤佳郁
                </h1>
                <p class="text-sm text-slate-300">
                  中共党员 · 前端实习生（AI 工程师方向）
                </p>
              </div>
            </div>
            <div
              class="mt-3 flex flex-wrap items-center gap-2 text-xs font-mono text-emerald-300"
            >
              <span class="rounded-full bg-slate-900/80 px-3 py-1">
                Typing: {{ typingDisplay }}
                <span
                  v-if="cursorVisible"
                  class="ml-1 inline-block h-4 w-[2px] translate-y-[1px] bg-emerald-400"
                />
              </span>
            </div>
          </div>
          <div
            class="w-full max-w-xs space-y-3 rounded-2xl border border-slate-700/80 bg-slate-900/80 px-4 py-4 text-sm backdrop-blur-xl md:w-72 no-print"
          >
            <div class="flex items-center justify-between gap-4">
              <span class="text-slate-400">意向</span>
              <span class="font-medium text-slate-100">
                前端实习生（AI 工程师方向）
              </span>
            </div>
            <div class="h-px bg-gradient-to-r from-slate-800 via-slate-700 to-slate-800" />
            <div class="space-y-1">
              <div class="flex items-center justify-between gap-4">
                <span class="text-slate-400">电话</span>
                <span class="font-medium text-slate-100">
                  17309160656
                </span>
              </div>
              <div class="flex items-center justify-between gap-4">
                <span class="text-slate-400">邮箱</span>
                <span class="truncate text-right font-medium text-slate-100">
                  2167406058@qq.com
                </span>
              </div>
              <div class="flex items-center justify-between gap-4">
                <span class="text-slate-400">GitHub</span>
                <a
                  href="https://github.com/NullPointerFun"
                  target="_blank"
                  rel="noreferrer"
                  class="truncate text-right text-emerald-300 hover:text-emerald-200"
                >
                  github.com/NullPointerFun
                </a>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section
        class="no-print rounded-2xl border border-slate-800 bg-slate-900/70 p-4 text-xs flex flex-col gap-3 md:flex-row md:items-center md:justify-between"
      >
        <div class="flex flex-wrap items-center gap-3">
          <div class="flex flex-col gap-1">
            <span class="text-slate-400">
              模板
            </span>
            <select
              v-model="state.templateKey"
              @change="onTemplateChange"
              class="rounded-md border border-slate-700 bg-slate-900 px-2 py-1 text-[11px] text-slate-100 focus:outline-none focus:ring-1 focus:ring-emerald-500"
            >
              <option
                v-for="tpl in templateOptions"
                :key="tpl.key"
                :value="tpl.key"
              >
                {{ tpl.label }}
              </option>
            </select>
          </div>
          <div class="flex flex-col gap-1">
            <span class="text-slate-400">
              主题
            </span>
            <select
              v-model="state.settings.theme"
              class="rounded-md border border-slate-700 bg-slate-900 px-2 py-1 text-[11px] text-slate-100 focus:outline-none focus:ring-1 focus:ring-emerald-500"
            >
              <option value="emerald">
                翡翠绿
              </option>
              <option value="violet">
                极光紫
              </option>
              <option value="cyan">
                霓虹蓝
              </option>
            </select>
          </div>
          <div class="flex flex-col gap-1">
            <span class="text-slate-400">
              字体
            </span>
            <select
              v-model="state.settings.fontFamily"
              class="rounded-md border border-slate-700 bg-slate-900 px-2 py-1 text-[11px] text-slate-100 focus:outline-none focus:ring-1 focus:ring-emerald-500"
            >
              <option value="sans">
                Sans
              </option>
              <option value="serif">
                Serif
              </option>
              <option value="mono">
                Mono
              </option>
            </select>
          </div>
          <div class="flex flex-col gap-1">
            <span class="text-slate-400">
              字号
            </span>
            <select
              v-model="state.settings.fontSize"
              class="rounded-md border border-slate-700 bg-slate-900 px-2 py-1 text-[11px] text-slate-100 focus:outline-none focus:ring-1 focus:ring-emerald-500"
            >
              <option value="sm">
                小
              </option>
              <option value="md">
                中
              </option>
              <option value="lg">
                大
              </option>
            </select>
          </div>
          <div class="flex flex-col gap-1">
            <span class="text-slate-400">
              模块间距
            </span>
            <select
              v-model="state.settings.spacing"
              class="rounded-md border border-slate-700 bg-slate-900 px-2 py-1 text-[11px] text-slate-100 focus:outline-none focus:ring-1 focus:ring-emerald-500"
            >
              <option value="compact">
                紧凑
              </option>
              <option value="normal">
                适中
              </option>
              <option value="relaxed">
                宽松
              </option>
            </select>
          </div>
        </div>
        <div class="flex flex-wrap items-center gap-3">
          <div class="flex flex-col gap-1">
            <span class="text-slate-400">
              自定义头像
            </span>
            <input
              type="file"
              accept="image/*"
              @change="onAvatarChange"
              class="block text-[11px] text-slate-300"
            />
          </div>
          <div class="flex flex-wrap gap-2">
            <button
              type="button"
              class="rounded-md border border-slate-700 bg-slate-900 px-3 py-1 text-[11px] text-slate-100 hover:bg-slate-800"
              @click="saveDraft"
            >
              保存草稿
            </button>
            <button
              type="button"
              class="rounded-md border border-slate-700 bg-slate-900 px-3 py-1 text-[11px] text-slate-100 hover:bg-slate-800"
              @click="exportJson"
            >
              导出 JSON
            </button>
            <button
              type="button"
              class="rounded-md border border-emerald-500/60 bg-emerald-500/10 px-3 py-1 text-[11px] text-emerald-200 hover:bg-emerald-500/20"
              @click="exportPdf"
            >
              导出 PDF
            </button>
            <button
              type="button"
              class="rounded-md border border-rose-500/60 bg-rose-500/10 px-3 py-1 text-[11px] text-rose-100 hover:bg-rose-500/20"
              @click="resetAll"
            >
              重置
            </button>
          </div>
        </div>
      </section>

      <section class="mt-4">
        <div
          class="relative overflow-hidden rounded-2xl border border-emerald-500/40 bg-slate-900/80 px-6 py-5 shadow-[0_0_35px_rgba(16,185,129,0.45)] backdrop-blur-xl ai-skill-matrix"
        >
          <div
            class="pointer-events-none absolute -top-16 left-0 h-40 w-40 rounded-full bg-emerald-400/20 blur-3xl"
          />
          <div
            class="pointer-events-none absolute -bottom-16 right-0 h-40 w-40 rounded-full bg-cyan-400/20 blur-3xl"
          />
          <div class="relative flex flex-col gap-4">
            <div class="flex items-center justify-between gap-4">
              <div>
                <h2
                  class="text-xs font-semibold tracking-[0.3em] text-emerald-200 uppercase"
                >
                  AI Skill Matrix
                </h2>
                <p class="mt-2 text-xs text-slate-300">
                  围绕大模型落地的核心能力：从 Prompt 设计到 Agent 编排，再到 API
                  调用与评估。
                </p>
              </div>
              <div
                class="hidden md:flex items-center gap-1 rounded-full border border-emerald-400/40 bg-slate-900/80 px-3 py-1 text-[11px] font-mono text-emerald-200"
              >
                <span class="h-1.5 w-1.5 rounded-full bg-emerald-400" />
                <span>AI-Oriented Frontend · 2026</span>
              </div>
            </div>
            <div class="grid gap-3 md:grid-cols-3 text-xs">
              <div class="ai-skill-pill">
                <div class="flex items-center justify-between gap-2">
                  <span class="font-medium text-slate-100">
                    Prompt Engineering
                  </span>
                  <span
                    class="rounded-full bg-emerald-500/15 px-2 py-0.5 text-[10px] font-mono text-emerald-200"
                  >
                    熟练
                  </span>
                </div>
                <p class="mt-2 text-[11px] text-slate-300">
                  能够根据业务目标拆解任务、设计多轮 Prompt 流程，并结合工具调用与约束引导模型输出稳定结果。
                </p>
              </div>

              <div class="ai-skill-pill">
                <div class="flex items-center justify-between gap-2">
                  <span class="font-medium text-slate-100">
                    AI Agent 开发
                  </span>
                  <span
                    class="rounded-full bg-cyan-500/15 px-2 py-0.5 text-[10px] font-mono text-cyan-200"
                  >
                    探索
                  </span>
                </div>
                <p class="mt-2 text-[11px] text-slate-300">
                  关注多 Agent 协作、工具调用与记忆管理等模式，具备在前端场景中集成 Agent
                  工作流的实践探索。
                </p>
              </div>

              <div class="ai-skill-pill">
                <div class="flex items-center justify-between gap-2">
                  <span class="font-medium text-slate-100">
                    大模型 API 调用
                  </span>
                  <span
                    class="rounded-full bg-violet-500/15 px-2 py-0.5 text-[10px] font-mono text-violet-200"
                  >
                    应用
                  </span>
                </div>
                <p class="mt-2 text-[11px] text-slate-300">
                  理解上下文窗口、流式输出与速率限制等概念，能够在前端协调后端 API 调用并做好错误兜底与重试策略。
                </p>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section
        class="no-print rounded-2xl border border-slate-800 bg-slate-900/70 p-4 text-xs"
      >
        <div class="flex items-center justify-between gap-3">
          <div class="flex items-center gap-2">
            <h2
              class="text-[11px] font-semibold tracking-[0.25em] text-slate-400 uppercase"
            >
              模块管理
            </h2>
            <button
              type="button"
              class="rounded-md border border-slate-700 bg-slate-900 px-2 py-1 text-[11px] text-slate-100 hover:bg-slate-800"
              @click="addCustomModule"
            >
              + 添加自定义模块
            </button>
          </div>
        </div>
        <ul class="mt-3 space-y-2">
          <li
            v-for="(module, index) in state.modules"
            :key="module.id"
            class="flex items-center justify-between gap-2 rounded-xl border border-slate-700/70 bg-slate-900/80 px-3 py-2"
            draggable="true"
            @dragstart="onDragStart(index)"
            @dragover.prevent
            @drop="onDrop(index)"
          >
            <div class="flex items-center gap-2">
              <span class="cursor-move text-slate-500">
                ≡
              </span>
              <span class="text-slate-100">
                {{ module.title }}
              </span>
              <span class="text-[10px] text-slate-500">
                {{ getModuleTypeLabel(module.type) }}
              </span>
            </div>
            <div class="flex items-center gap-2">
              <button
                type="button"
                class="rounded-md border border-slate-700 bg-slate-900 px-2 py-1 text-[10px] text-slate-100 hover:bg-slate-800"
                @click="toggleModule(module.id)"
              >
                {{ module.enabled ? "隐藏" : "显示" }}
              </button>
              <button
                type="button"
                class="rounded-md border border-rose-500/60 bg-rose-500/10 px-2 py-1 text-[10px] text-rose-100 hover:bg-rose-500/20"
                @click="removeModule(module.id)"
              >
                删除
              </button>
            </div>
          </li>
        </ul>
      </section>

      <section :class="['mt-2', previewSpacingClass]">
        <div
          v-for="module in enabledModules"
          :key="module.id"
          class="space-y-3"
        >
          <div v-if="module.type === 'education'">
            <div
              class="rounded-2xl border border-slate-800 bg-slate-900/70 p-6 backdrop-blur-md shadow-[0_0_25px_rgba(15,23,42,0.8)]"
            >
              <h2
                class="text-xs font-semibold tracking-[0.3em] text-slate-400 uppercase"
              >
                教育背景
              </h2>
              <div class="mt-4 space-y-2">
                <div
                  class="flex flex-col justify-between gap-1 md:flex-row md:items-baseline"
                >
                  <div class="text-base font-medium text-slate-100">
                    桂林信息科技学院 · 软件工程（本科）
                  </div>
                  <div class="text-sm text-slate-400">
                    2022 – 2026 届
                  </div>
                </div>
                <p class="text-sm text-slate-400">
                  系统学习软件工程、计算机网络、数据结构与算法、数据库系统、人工智能等课程，关注前端工程化与 AI
                  在业务中的落地实践。
                </p>
              </div>
            </div>
          </div>

          <div v-else-if="module.type === 'honors'">
            <section>
              <h2
                class="text-xs font-semibold tracking-[0.3em] text-slate-400 uppercase"
              >
                竞赛荣誉
              </h2>
              <div class="mt-4 grid gap-4 md:grid-cols-3">
                <article class="experience-card">
                  <div class="flex items-center justify-between gap-2">
                    <h3 class="text-sm font-medium text-slate-100">
                      蓝桥杯 C/C++
                    </h3>
                    <span
                      class="rounded-full bg-emerald-500/10 px-2 py-0.5 text-xs font-mono text-emerald-300"
                    >
                      省三
                    </span>
                  </div>
                  <p class="mt-2 text-xs text-slate-400">
                    第十五届蓝桥杯 C/C++ 程序设计赛道，扎实的算法与编码能力。
                  </p>
                </article>
                <article class="experience-card">
                  <div class="flex items-center justify-between gap-2">
                    <h3 class="text-sm font-medium text-slate-100">
                      华为 ICT 大赛
                    </h3>
                    <span
                      class="rounded-full bg-emerald-500/10 px-2 py-0.5 text-xs font-mono text-emerald-300"
                    >
                      省二
                    </span>
                  </div>
                  <p class="mt-2 text-xs text-slate-400">
                    第九届华为 ICT 大赛基础软件赛道，强化对基础软件与工程实践的理解。
                  </p>
                </article>
                <article class="experience-card">
                  <div class="flex items-center justify-between gap-2">
                    <h3 class="text-sm font-medium text-slate-100">
                      全国大学生英语竞赛
                    </h3>
                    <span
                      class="rounded-full bg-emerald-500/10 px-2 py-0.5 text-xs font-mono text-emerald-300"
                    >
                      省三
                    </span>
                  </div>
                  <p class="mt-2 text-xs text-slate-400">
                    具备良好的英文阅读与沟通能力，利于理解前沿 AI 论文与文档。
                  </p>
                </article>
                <article class="experience-card">
                  <div class="flex items-center justify-between gap-2">
                    <h3 class="text-sm font-medium text-slate-100">
                      三维数字化创新设计
                    </h3>
                    <span
                      class="rounded-full bg-emerald-500/10 px-2 py-0.5 text-xs font-mono text-emerald-300"
                    >
                      省三
                    </span>
                  </div>
                  <p class="mt-2 text-xs text-slate-400">
                    全国三维数字化创新设计大赛，具备空间思维与产品设计意识。
                  </p>
                </article>
                <article class="experience-card md:col-span-2">
                  <div class="flex items-center justify-between gap-2">
                    <h3 class="text-sm font-medium text-slate-100">
                      校园排舞展示大赛
                    </h3>
                    <span
                      class="rounded-full bg-emerald-500/10 px-2 py-0.5 text-xs font-mono text-emerald-300"
                    >
                      国三
                    </span>
                  </div>
                  <p class="mt-2 text-xs text-slate-400">
                    2023 年全国大学生校园排舞展示大赛，体现团队协作与舞台表现力。
                  </p>
                </article>
              </div>
            </section>
          </div>

          <div v-else-if="module.type === 'experience'">
            <section class="grid gap-6 md:grid-cols-2">
              <article class="experience-card">
                <div class="flex items-center justify-between gap-2">
                  <h2 class="text-sm font-semibold text-slate-100">
                    陕西正见生态 · 前端实习
                  </h2>
                  <span class="text-xs text-slate-400">
                    智慧农业 IoT 平台
                  </span>
                </div>
                <p class="mt-3 text-xs text-slate-400">
                  参与智慧农业 IoT 平台的前端研发，基于 Vue
                  构建数据可视化大屏，展示传感器数据、设备状态与告警信息。
                </p>
                <ul class="mt-3 space-y-1.5 text-xs text-slate-300">
                  <li>
                    负责大屏页面的布局与组件拆分，保证复杂信息在大屏上的清晰呈现。
                  </li>
                  <li>
                    协助对接后端接口与实时数据流，优化渲染性能与交互体验。
                  </li>
                </ul>
                <div class="mt-4 flex flex-wrap gap-2 text-[10px]">
                  <span class="tag-chip">
                    Vue 3
                  </span>
                  <span class="tag-chip">
                    数据可视化
                  </span>
                  <span class="tag-chip">
                    IoT 场景
                  </span>
                </div>
              </article>

              <article class="experience-card">
                <div class="flex items-center justify-between gap-2">
                  <h2 class="text-sm font-semibold text-slate-100">
                    校园废品回收系统 · 大创项目
                  </h2>
                  <span class="text-xs text-slate-400">
                    前后端协同实践
                  </span>
                </div>
                <p class="mt-3 text-xs text-slate-400">
                  负责前端核心模块与自动化测试相关工作，聚焦校园场景下的废品回收流程优化。
                </p>
                <ul class="mt-3 space-y-1.5 text-xs text-slate-300">
                  <li>
                    使用 Vue 3 + TypeScript 实现动态表单与订单流转界面。
                  </li>
                  <li>
                    设计并优化 Selenium 测试脚本，减少约 30% 重复用例，提升回归效率。
                  </li>
                </ul>
                <div class="mt-4 flex flex-wrap gap-2 text-[10px]">
                  <span class="tag-chip">
                    Vue 3
                  </span>
                  <span class="tag-chip">
                    TypeScript
                  </span>
                  <span class="tag-chip">
                    Spring Boot
                  </span>
                  <span class="tag-chip">
                    Selenium 自动化测试
                  </span>
                </div>
              </article>
            </section>
          </div>

          <div v-else-if="module.type === 'ai_collab'">
            <section>
              <article
                class="relative overflow-hidden rounded-2xl border border-emerald-500/40 bg-gradient-to-r from-slate-900/90 via-slate-900/80 to-emerald-900/40 p-6 backdrop-blur-xl shadow-[0_0_35px_rgba(16,185,129,0.45)]"
              >
                <div
                  class="pointer-events-none absolute -top-16 right-10 h-40 w-40 rounded-full bg-emerald-400/20 blur-3xl"
                />
                <div class="relative space-y-3">
                  <div
                    class="inline-flex items-center gap-2 rounded-full bg-slate-900/80 px-3 py-1 text-[11px] font-mono uppercase tracking-[0.25em] text-emerald-200"
                  >
                    <span class="h-1.5 w-1.5 rounded-full bg-emerald-400" />
                    <span>AI Collaboration</span>
                  </div>
                  <h2 class="text-sm font-semibold text-emerald-100">
                    AI 协作实战声明
                  </h2>
                  <p class="text-xs text-slate-200 leading-relaxed">
                    本项目通过 Trae 的 AI Builder 模式深度协作完成，过程中围绕简历结构设计、Tailwind
                    视觉体系和交互动效进行多轮迭代，展示了高效的 Prompt Engineering 与问题解决能力。
                  </p>
                  <p class="text-xs text-slate-300">
                    包含对脚手架初始化异常（如 npm 命名冲突）的分析和手动修复，以及对组件结构与样式的快速重构，体现了在真实开发环境中与
                    AI 协作完成工程任务的实践经验。
                  </p>
                </div>
              </article>
            </section>
          </div>

          <div v-else-if="module.type === 'custom'">
            <article class="experience-card">
              <h2 class="text-sm font-semibold text-slate-100">
                {{ module.title }}
              </h2>
              <p class="mt-3 text-xs text-slate-300">
                {{ module.content }}
              </p>
            </article>
          </div>
        </div>
      </section>
    </main>
  </div>
</template>

<script setup>
import { computed, onMounted, onUnmounted, ref } from "vue";

const STORAGE_KEY = "ai-resume-builder-state";
const fullTypingText = "AI 工程师 · 前端实习生简历正在生成中";

const defaultState = () => ({
  templateKey: "ai-dark",
  settings: {
    fontFamily: "sans",
    fontSize: "md",
    spacing: "normal",
    theme: "emerald"
  },
  avatarDataUrl: "",
  modules: [
    { id: "education", type: "education", title: "教育背景", enabled: true },
    { id: "honors", type: "honors", title: "竞赛荣誉", enabled: true },
    {
      id: "experience",
      type: "experience",
      title: "实习 / 项目经历",
      enabled: true
    },
    {
      id: "ai-collab",
      type: "ai_collab",
      title: "AI 协作实战声明",
      enabled: true
    }
  ]
});

const state = ref(defaultState());

const typingDisplay = ref("");
const cursorVisible = ref(true);

const templateOptions = [
  { key: "ai-dark", label: "AI 工程师 · 深色模板" },
  { key: "clean-dark", label: "极简深色模板" }
];

const draggingIndex = ref(null);
let typingIntervalId;
let cursorIntervalId;

const themeClass = computed(() => {
  const theme = state.value.settings.theme;
  if (theme === "violet") return "theme-violet";
  if (theme === "cyan") return "theme-cyan";
  return "theme-emerald";
});

const enabledModules = computed(() =>
  state.value.modules.filter(m => m && m.enabled)
);

const fontClass = computed(() => {
  const font = state.value.settings.fontFamily;
  if (font === "serif") return "font-serif";
  if (font === "mono") return "font-mono";
  return "font-sans";
});

const mainTextSizeClass = computed(() => {
  const size = state.value.settings.fontSize;
  if (size === "sm") return "text-[13px]";
  if (size === "lg") return "text-[15px]";
  return "text-[14px]";
});

const previewSpacingClass = computed(() => {
  const spacing = state.value.settings.spacing;
  if (spacing === "compact") return "space-y-4";
  if (spacing === "relaxed") return "space-y-8";
  return "space-y-6";
});

const heroBorderClass = computed(() => {
  const theme = state.value.settings.theme;
  if (theme === "violet") {
    return "border-violet-500/30 shadow-[0_0_40px_rgba(139,92,246,0.35)]";
  }
  if (theme === "cyan") {
    return "border-cyan-500/30 shadow-[0_0_40px_rgba(34,211,238,0.35)]";
  }
  return "border-emerald-500/20 shadow-[0_0_40px_rgba(16,185,129,0.25)]";
});

const heroAccentBorderClass = computed(() => {
  const theme = state.value.settings.theme;
  if (theme === "violet") return "border-violet-400/50";
  if (theme === "cyan") return "border-cyan-400/50";
  return "border-emerald-400/40";
});

const heroBadgeClass = computed(() => {
  const theme = state.value.settings.theme;
  if (theme === "violet") {
    return "border-violet-400/40 bg-violet-500/10 text-violet-200";
  }
  if (theme === "cyan") {
    return "border-cyan-400/40 bg-cyan-500/10 text-cyan-200";
  }
  return "border-emerald-400/40 bg-emerald-500/10 text-emerald-300";
});

function getModuleTypeLabel(type) {
  if (type === "education") return "教育";
  if (type === "honors") return "荣誉";
  if (type === "experience") return "实习 / 项目";
  if (type === "ai_collab") return "AI 协作";
  if (type === "custom") return "自定义";
  return type;
}

function onAvatarChange(event) {
  const file = event.target.files && event.target.files[0];
  if (!file) return;
  const reader = new FileReader();
  reader.onload = e => {
    const result = e.target && e.target.result;
    if (typeof result === "string") {
      state.value.avatarDataUrl = result;
    }
  };
  reader.readAsDataURL(file);
}

function addCustomModule() {
  const id = `custom-${Date.now()}`;
  state.value.modules.push({
    id,
    type: "custom",
    title: "自定义模块",
    enabled: true,
    content: "在这里描述你的额外经历、技能或项目亮点。"
  });
}

function toggleModule(id) {
  const target = state.value.modules.find(m => m.id === id);
  if (!target) return;
  target.enabled = !target.enabled;
}

function removeModule(id) {
  state.value.modules = state.value.modules.filter(m => m.id !== id);
}

function onDragStart(index) {
  draggingIndex.value = index;
}

function onDrop(targetIndex) {
  const from = draggingIndex.value;
  if (from === null || from === targetIndex) return;
  const list = [...state.value.modules];
  const moved = list.splice(from, 1)[0];
  list.splice(targetIndex, 0, moved);
  state.value.modules = list;
  draggingIndex.value = null;
}

function saveDraft() {
  window.localStorage.setItem(STORAGE_KEY, JSON.stringify(state.value));
}

function loadDraftIfExists() {
  const raw = window.localStorage.getItem(STORAGE_KEY);
  if (!raw) return;
  try {
    const parsed = JSON.parse(raw);
    const base = defaultState();
    state.value = Object.assign(base, parsed, {
      settings: Object.assign(base.settings, parsed.settings || {}),
      modules: parsed.modules || base.modules
    });
  } catch {
  }
}

function resetAll() {
  state.value = defaultState();
  window.localStorage.removeItem(STORAGE_KEY);
}

function exportJson() {
  const dataStr = JSON.stringify(state.value, null, 2);
  const blob = new Blob([dataStr], { type: "application/json" });
  const url = URL.createObjectURL(blob);
  const a = document.createElement("a");
  a.href = url;
  a.download = "resume.json";
  document.body.appendChild(a);
  a.click();
  document.body.removeChild(a);
  URL.revokeObjectURL(url);
}

function exportPdf() {
  window.print();
}

function onTemplateChange() {
  const key = state.value.templateKey;
  if (key === "clean-dark") {
    state.value.settings.theme = "cyan";
    state.value.settings.spacing = "relaxed";
  } else {
    state.value.settings.theme = "emerald";
    state.value.settings.spacing = "normal";
  }
}

function startTypingEffect() {
  let index = 0;
  typingIntervalId = window.setInterval(() => {
    if (index <= fullTypingText.length) {
      typingDisplay.value = fullTypingText.slice(0, index);
      index += 1;
    } else {
      window.clearInterval(typingIntervalId);
    }
  }, 90);
  cursorIntervalId = window.setInterval(() => {
    cursorVisible.value = !cursorVisible.value;
  }, 450);
}

onMounted(() => {
  loadDraftIfExists();
  startTypingEffect();
});

onUnmounted(() => {
  if (typingIntervalId) {
    window.clearInterval(typingIntervalId);
  }
  if (cursorIntervalId) {
    window.clearInterval(cursorIntervalId);
  }
});
</script>
