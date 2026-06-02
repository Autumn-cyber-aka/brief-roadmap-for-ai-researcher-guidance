<script setup>
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
    <a class="brand" href="#top">
      <span class="brand-index">MIC / 01</span>
      <strong>Minimum AI Curriculum</strong>
    </a>
    <nav class="main-nav" aria-label="主导航">
      <a href="#foundations">01 基础</a>
      <a href="#core">02 核心</a>
      <a href="#specializations">03 方向</a>
    </nav>
  </header>

  <main id="top">
    <section class="hero page-shell">
      <p class="kicker">A MINIMUM PATH TO AI RESEARCH</p>
      <h1>
        Learn less.<br />
        <span>Understand more.</span>
      </h1>
      <div class="hero-bottom">
        <p>
          一份尽可能短的 AI 自学课程表。<br />
          从编程基础开始，逐步获得成为 AI researcher 所需的核心能力。
        </p>
        <a class="arrow-link" href="#foundations">开始学习 <span>↓</span></a>
      </div>
      <p class="hero-note">THREE STAGES · ONE RESEARCH DIRECTION · NO DETOURS</p>
    </section>

    <section id="foundations" class="curriculum-section page-shell">
      <div class="section-intro">
        <p class="section-number">01</p>
        <div>
          <p class="kicker">FOUNDATIONS / 基础能力</p>
          <h2>建立可以继续学习的最低基础。</h2>
          <p class="section-description">
            不需要先修完一整套计算机科学课程。掌握以下内容，就可以进入 AI 主线。
          </p>
        </div>
      </div>

      <div class="card-grid foundations-grid">
        <article v-for="item in foundations" :key="item.code" class="curriculum-card">
          <p class="card-code">{{ item.code }}</p>
          <h3>{{ item.title }}</h3>
          <p class="card-subtitle">{{ item.titleZh }}</p>
          <ul>
            <li v-for="topic in item.topics" :key="topic">{{ topic }}</li>
          </ul>
          <div class="outcome">
            <span>完成标准 / OUTCOME</span>
            <p>{{ item.outcome }}</p>
          </div>
        </article>
      </div>
    </section>

    <section id="core" class="curriculum-section core-section">
      <div class="page-shell">
        <div class="section-intro">
          <p class="section-number">02</p>
          <div>
            <p class="kicker">CORE / AI 基础</p>
            <h2>用一门课程建立机器学习主干。</h2>
            <p class="section-description">
              这一阶段只保留一条主线：Stanford CS229。它提供理解后续细分方向所需的共同语言。
            </p>
          </div>
        </div>

        <article class="core-card">
          <div class="core-heading">
            <div>
              <p class="card-code">C.01 · REQUIRED</p>
              <h3>Stanford CS229</h3>
              <p class="card-subtitle">Machine Learning / 机器学习</p>
            </div>
            <a
              class="external-link"
              href="https://cs229.stanford.edu/"
              target="_blank"
              rel="noopener noreferrer"
            >
              官方课程 <span>↗</span>
            </a>
          </div>
          <div class="core-body">
            <ul class="topic-list">
              <li v-for="topic in coreTopics" :key="topic">{{ topic }}</li>
            </ul>
            <div class="outcome">
              <span>完成标准 / OUTCOME</span>
              <p>能够理解经典机器学习方法，训练基础模型，并判断评估结果是否可信。</p>
            </div>
          </div>
        </article>
      </div>
    </section>

    <section id="specializations" class="curriculum-section page-shell">
      <div class="section-intro">
        <p class="section-number">03</p>
        <div>
          <p class="kicker">SPECIALIZATION / 选择一个研究方向</p>
          <h2>选一条路，开始深入。</h2>
          <p class="section-description">
            三门课并列，任选其一。不要同时开始所有方向；先在一个具体问题域中建立研究判断力。
          </p>
        </div>
      </div>

      <div class="card-grid specialization-grid">
        <a
          v-for="item in specializations"
          :key="item.code"
          class="specialization-card"
          :href="item.href"
          target="_blank"
          rel="noopener noreferrer"
        >
          <p class="card-code">{{ item.code }} · ELECTIVE</p>
          <h3>{{ item.title }}</h3>
          <p class="card-subtitle">{{ item.titleZh }}</p>
          <div class="specialization-footer">
            <div>
              <strong>{{ item.course }}</strong>
              <p>{{ item.description }}</p>
            </div>
            <span class="external-arrow">↗</span>
          </div>
        </a>
      </div>
    </section>

    <section class="principles-section">
      <div class="page-shell principles-layout">
        <div>
          <p class="kicker">DESIGN PRINCIPLES / 学习原则</p>
          <h2>The shortest useful path.</h2>
        </div>
        <div class="principles-list">
          <div v-for="[number, title, text] in principles" :key="number" class="principle">
            <span>{{ number }}</span>
            <div>
              <h3>{{ title }}</h3>
              <p>{{ text }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </main>

  <footer class="site-footer">
    <div class="page-shell footer-layout">
      <div>
        <strong>Minimum AI Curriculum</strong>
        <p>A minimum path to AI research.</p>
      </div>
      <a href="#top">BACK TO TOP ↑</a>
    </div>
  </footer>
</template>
