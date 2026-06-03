<script setup>
import { nextTick } from "vue";

const scrollTo = async (href) => {
  if (!href.startsWith("#")) return;

  const targetId = href.slice(1);
  history.pushState(null, "", href);
  await nextTick();

  if (targetId === "top") {
    window.scrollTo({ top: 0, behavior: "smooth" });
    return;
  }

  document.getElementById(targetId)?.scrollIntoView({ behavior: "smooth", block: "start" });
};

const sidebarSections = [
  {
    title: "路线总览",
    links: [
      { label: "开始阅读", href: "#top" },
      { label: "如何使用", href: "#how-to-use" },
    ],
  },
  {
    title: "课程目录",
    links: [
      { label: "基础能力", href: "#foundations" },
      { label: "AI 核心", href: "#core" },
      { label: "研究方向", href: "#specializations" },
      { label: "学习原则", href: "#principles" },
    ],
  },
];

const pageToc = [
  { label: "路线目标", href: "#top" },
  { label: "如何使用", href: "#how-to-use" },
  { label: "基础能力", href: "#foundations" },
  { label: "AI 核心", href: "#core" },
  { label: "研究方向", href: "#specializations" },
  { label: "学习原则", href: "#principles" },
];

const foundations = [
  {
    code: "F.01",
    title: "Programming",
    titleZh: "编程入门",
    topics: ["Python 科学计算基础", "C++ 语法与 STL", "调试、测试与版本控制"],
    outcome: "能够独立实现小型程序，并把数学想法转化为可运行的实验代码。",
  },
  {
    code: "F.02",
    title: "Discrete Mathematics",
    titleZh: "离散数学",
    topics: ["逻辑与集合", "组合计数", "图论基础", "证明方法"],
    outcome: "能够准确描述问题、阅读证明，并理解算法背后的离散结构。",
  },
  {
    code: "F.03",
    title: "Data Structures & Algorithms",
    titleZh: "数据结构与算法",
    topics: ["常见数据结构", "排序与搜索", "递归与动态规划", "时间与空间复杂度"],
    outcome: "能够选择合适的数据结构，分析复杂度，并写出可靠的基础算法。",
  },
];

const coreTopics = [
  "Supervised Learning / 监督学习",
  "Learning Theory / 学习理论",
  "Unsupervised Learning / 无监督学习",
  "Reinforcement Learning / 强化学习基础",
];

const specializations = [
  {
    code: "S.01",
    title: "Natural Language Processing",
    titleZh: "自然语言处理",
    course: "Stanford CS224N",
    description: "Natural Language Processing with Deep Learning",
    href: "https://web.stanford.edu/class/cs224n/",
  },
  {
    code: "S.02",
    title: "Computer Vision",
    titleZh: "计算机视觉",
    course: "Stanford CS231N",
    description: "Deep Learning for Computer Vision",
    href: "https://cs231n.stanford.edu/",
  },
  {
    code: "S.03",
    title: "Language Modeling",
    titleZh: "语言模型",
    course: "Stanford CS336",
    description: "Language Modeling from Scratch · Spring 2026",
    href: "https://stanford-cs336.github.io/spring2026/",
  },
];

const principles = [
  ["01", "Learn the minimum", "只学习进入下一阶段真正需要的内容。"],
  ["02", "Build understanding", "目标不是收藏课程，而是获得独立理解问题的能力。"],
  ["03", "Choose one direction", "完成共同基础后，选择一个方向深入，而不是同时铺开。"],
];
</script>

<template>
  <header class="site-header">
    <a class="brand" href="#top" @click.prevent="scrollTo('#top')">
      <span class="brand-mark">AI</span>
      <span>
        <strong>Minimum AI Curriculum</strong>
        <small>Brief roadmap for AI researcher guidance</small>
      </span>
    </a>
    <nav class="header-nav" aria-label="顶部导航">
      <a href="#foundations" @click.prevent="scrollTo('#foundations')">课程目录</a>
      <a href="https://github.com/Autumn-cyber-aka/brief-roadmap-for-ai-researcher-guidance" target="_blank" rel="noopener noreferrer">
        GitHub
      </a>
    </nav>
  </header>

  <div class="docs-layout">
    <aside class="sidebar" aria-label="课程目录">
      <nav v-for="section in sidebarSections" :key="section.title" class="sidebar-group">
        <p>{{ section.title }}</p>
        <a
          v-for="link in section.links"
          :key="link.href"
          :href="link.href"
          @click.prevent="scrollTo(link.href)"
        >
          {{ link.label }}
        </a>
      </nav>
    </aside>

    <main id="top" class="docs-main">
      <section class="doc-hero">
        <p class="eyebrow">AI RESEARCHER ROADMAP</p>
        <h1>一份尽可能短的 AI 自学路线。</h1>
        <p class="lead">
          从编程、离散数学、数据结构与算法开始，进入机器学习主线，再选择一个研究方向深入。
          这不是课程收藏夹，而是一条尽量少绕路的学习路径。
        </p>
        <div class="hero-actions">
          <a class="primary-link" href="#foundations" @click.prevent="scrollTo('#foundations')">
            查看课程目录
          </a>
          <a class="secondary-link" href="#how-to-use" @click.prevent="scrollTo('#how-to-use')">
            阅读使用方式
          </a>
        </div>
      </section>

      <section id="how-to-use" class="doc-section">
        <p class="section-label">Overview</p>
        <h2>如何使用这份路线</h2>
        <p>
          先完成共同基础，再学习一门机器学习核心课程，最后只选择一个方向深入。
          如果某个阶段已经掌握，可以直接跳过；如果没有把握，就用每个条目的“完成标准”自查。
        </p>
        <div class="notice">
          <strong>建议节奏</strong>
          <span>不要同时铺开所有方向。先让自己具备读论文、复现实验、判断结果是否可信的基本能力。</span>
        </div>
      </section>

      <section id="foundations" class="doc-section">
        <p class="section-label">01 Foundations</p>
        <h2>基础能力</h2>
        <p>
          不需要先修完一整套计算机科学课程。下面三项是进入 AI 主线前最有用的最低基础。
        </p>

        <div class="course-list">
          <article v-for="item in foundations" :key="item.code" class="course-card">
            <div class="course-meta">
              <span>{{ item.code }}</span>
              <strong>{{ item.titleZh }}</strong>
            </div>
            <div class="course-body">
              <h3>{{ item.title }}</h3>
              <ul>
                <li v-for="topic in item.topics" :key="topic">{{ topic }}</li>
              </ul>
              <div class="outcome">
                <span>完成标准</span>
                <p>{{ item.outcome }}</p>
              </div>
            </div>
          </article>
        </div>
      </section>

      <section id="core" class="doc-section">
        <p class="section-label">02 Core</p>
        <h2>AI 核心</h2>
        <p>
          这一阶段只保留一条主线：Stanford CS229。它提供理解后续细分方向所需的共同语言。
        </p>

        <article class="course-card highlighted-card">
          <div class="course-meta">
            <span>C.01</span>
            <strong>Required</strong>
          </div>
          <div class="course-body">
            <h3>Stanford CS229</h3>
            <p class="course-subtitle">Machine Learning / 机器学习</p>
            <ul>
              <li v-for="topic in coreTopics" :key="topic">{{ topic }}</li>
            </ul>
            <div class="outcome">
              <span>完成标准</span>
              <p>能够理解经典机器学习方法，训练基础模型，并判断评估结果是否可信。</p>
            </div>
            <a class="resource-link" href="https://cs229.stanford.edu/" target="_blank" rel="noopener noreferrer">
              打开官方课程 ↗
            </a>
          </div>
        </article>
      </section>

      <section id="specializations" class="doc-section">
        <p class="section-label">03 Specialization</p>
        <h2>选择一个研究方向</h2>
        <p>
          三门课并列，任选其一。重点不是同时学完所有方向，而是在一个具体问题域中建立研究判断力。
        </p>

        <div class="resource-grid">
          <a
            v-for="item in specializations"
            :key="item.code"
            class="resource-card"
            :href="item.href"
            target="_blank"
            rel="noopener noreferrer"
          >
            <span>{{ item.code }}</span>
            <h3>{{ item.title }}</h3>
            <p>{{ item.titleZh }}</p>
            <strong>{{ item.course }}</strong>
            <small>{{ item.description }}</small>
          </a>
        </div>
      </section>

      <section id="principles" class="doc-section">
        <p class="section-label">Principles</p>
        <h2>学习原则</h2>
        <div class="principles-list">
          <article v-for="[number, title, text] in principles" :key="number" class="principle">
            <span>{{ number }}</span>
            <div>
              <h3>{{ title }}</h3>
              <p>{{ text }}</p>
            </div>
          </article>
        </div>
      </section>
    </main>

    <aside class="page-toc" aria-label="本页目录">
      <p>本页目录</p>
      <a
        v-for="link in pageToc"
        :key="link.href"
        :href="link.href"
        @click.prevent="scrollTo(link.href)"
      >
        {{ link.label }}
      </a>
    </aside>
  </div>

  <footer class="site-footer">
    <span>Minimum AI Curriculum</span>
    <a href="#top" @click.prevent="scrollTo('#top')">Back to top ↑</a>
  </footer>
</template>
