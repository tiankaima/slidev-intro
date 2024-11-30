---
theme: seriph
background: https://cover.sli.dev
title: Welcome to Slidev
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
mdc: true
colorSchema: dark
---

# Welcome to Slidev

Presentation slides for developers

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" flex="~ justify-center items-center gap-2" hover="bg-white bg-opacity-10">
    Press Space for next page <div class="i-carbon:arrow-right inline-block"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <div class="i-carbon:edit" />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" alt="GitHub" title="Open in GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

---
transition: fade-out
layout: intro
class: mx-10
---

# \_Kerman {.font-mono.text-primary}

<div class="leading-8 opacity-80">
Slidev 团队成员 <br>
USTC 本科 2023级
</div>

<div my-16 w-min grid="~ cols-[40px_1fr] gap-y4" items-center justify-center ml--3>
  <div i-ri-github-line op50 ma text-xl/>
  <div><a href="https://github.com/KermanX" target="_blank">github.com/KermanX</a></div>
  <div i-ri-twitter-x-line op50 ma text-xl/>
  <div><a href="https://x.com/KermanX_" target="_blank">x.com/KermanX_</a></div>
  <div i-ri-bluesky-line op50 ma text-xl/>
  <div><a href="https://bsky.app/profile/kermanx.github.io" target="_blank">bsky.app/profile/KermanX.github.io</a></div>
</div>

<img src="./assets/avatar.jpg" rounded-full w-46 abs-tr mt-24 mr-48/>

<div flex="~ gap2">

</div>

---
transition: fade-out
layout: section
---

<div text-5xl pb-2>

Yet Another 

</div>

# Slides Maker?

---

<div grid grid-cols-2 gap-4 h-full>
<div>

## Basic slides things

```md
# Hello, Slidev

- Bullet 1
- Bullet 2

---

# Slide 2

<img src="https://sli.dev/logo-title.png" w-20 />
```

</div>
<div h-full grid grid-rows-2>

<SlideContainer w-full>
<DemoSlide>
<Cover>
  <h1>Hello, Slidev</h1>
  <ul>
    <li>Bullet 1</li>
    <li>Bullet 2</li>
  </ul>
</Cover>
</DemoSlide>
</SlideContainer>

<SlideContainer>
<DemoSlide>
<Default>
  <h1>Slide 2</h1>
  <img src="https://sli.dev/logo-title.png" w-64 />
</Default>
</DemoSlide>
</SlideContainer>

</div>
</div>

<script setup>
import Cover from '@slidev/client/layouts/cover.vue'
import Default from '@slidev/client/layouts/default.vue'
</script>

---
clicks: 3
---

## Code? <span v-click="2"> Even editable! </span>

<div v-show="$clicks < 2">

````md magic-move
```cpp
#include <stdio.h>

int main() {
  printf("Hello, Slidev!\n");

  for (int i = 0; i < 10; i++) {
    printf("%d\n", i);
  }
}
```

```cpp
#include <iostream>

int main() {
  std::cout << "Hello, Slidev!" << std::endl;

  for (int i : std::views::iota(0, 10)) {
    std::cout << i << std::endl;
  }
}
```
````

</div>

<div v-show="$clicks >= 2">

```cpp {monaco}
#include <iostream>

int main() {
  std::cout << "Hello, Slidev!" << std::endl;

  for (int i : std::views::iota(0, 10)) {
    std::cout << i << std::endl;
  }
}
```

</div>

---

## Interactivity?

<Connections class="mt-4"/>

<!-- <iframe v-click fixed right-0 w-120 h-68 top-30  src="https://sli.dev" ></iframe> -->

<iframe v-click fixed right-10 w-120 h-68 top-30 bottom-0  src="https://www.youtube.com/embed/dQw4w9WgXcQ?si=hCnWGH-S8ML-hjau" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

---

## Animation?

```html
<div
  v-motion
  :initial="{ x: -80 }"
  :enter="{ x: 0 }"
  :click-3="{ x: 80 }"
  :leave="{ x: 1000 }"
>
  Slidev
</div>
```

<div class="w-60 relative">
  <div class="relative w-40 h-40">
    <img
      v-motion
      :initial="{ x: 800, y: -100, scale: 1.5, rotate: -50 }"
      :enter="final"
      class="absolute inset-0"
      src="https://sli.dev/logo-square.png"
      alt=""
    />
    <img
      v-motion
      :initial="{ y: 500, x: -100, scale: 2 }"
      :enter="final"
      class="absolute inset-0"
      src="https://sli.dev/logo-circle.png"
      alt=""
    />
    <img
      v-motion
      :initial="{ x: 600, y: 400, scale: 2, rotate: 100 }"
      :enter="final"
      class="absolute inset-0"
      src="https://sli.dev/logo-triangle.png"
      alt=""
    />
  </div>

  <div
    class="text-5xl absolute top-14 left-40 text-[#2B90B6] -z-1"
    v-motion
    :initial="{ x: -80, opacity: 0}"
    :enter="{ x: 0, opacity: 1, transition: { delay: 2000, duration: 1000 } }">
    Slidev
  </div>
</div>

<!-- vue script setup scripts can be directly used in markdown, and will only affects current page -->
<script setup lang="ts">
const final = {
  x: 0,
  y: 0,
  rotate: 0,
  scale: 1,
  transition: {
    type: 'spring',
    damping: 10,
    stiffness: 20,
    mass: 2
  }
}
</script>


---
layout: section
---

<h1>
<span class="text-white!"> Your First </span>
<span class="slidev"> Slidev </span>
</h1>

<style>
.slidev {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 80%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

<div op-80> Option 1: </div>

# Stackblitz 在线环境

<div />

<div font-bold text-2xl class="font-[Consolas]" border="b dashed" w-min> sli.dev/new </div>

<div float-right mt--16>

优点：无需任何配置，只需要浏览器

缺点：速度不如本地环境

</div>

<img src="./assets/stackblitz.png" />

---

<div op-80> Option 2: </div>

# 本地环境

<div />

1. 安装 Node.js

    - 打开 https://nodejs.org/
    - 点击下载按钮并安装

2. 换源 (可选)

    打开终端，运行以下命令

```bash
  npm config set registry https://registry.npmmirror.com
```

---

<div op-80> 本地环境 </div>

# 创建 Slidev 项目

- 打开终端

- 创建 Slidev 项目

```bash
  npm create slidev@latest
```

- 进入项目目录

```bash
  cd my-slidev
```

- 打开 VSCode

```bash
  code .
```

---

<div op-80> 本地环境 </div>

# 运行 Slidev

<div />

打开终端（推荐使用 VSCode 内置终端），执行以下命令：

```bash
npm run dev
```

会自动打开一个浏览器窗口，显示你的幻灯片

尝试编辑 `slides.md` 文件，保存后浏览器会自动更新内容

---

<div op-80> 本地环境 </div>

# VSCode 拓展

<div />

搜索 “Slidev”，安装拓展

<v-clicks at="1">

- [点击 Slidev 图标]{.text-red}
- [幻灯片导航]{.text-yellow}
- [幻灯片预览]{.text-green}

</v-clicks>

<img src="./assets/vscode.png" fixed right-0 top-0 bottom-0 h-full />

<div v-click border="2 red rounded" v-drag="[510,283,44,43]" />

<div v-click border="2 yellow rounded" v-drag="[555,22,216,300]" />

<div v-click border="2 green rounded" v-drag="[555,323,216,214]" />

---

# 用户界面

<div />

- 导航幻灯片：
  
    - 左右键：上一步/下一步
    - 空格：下一步
    - 左右键：上一张/下一张
    - 左下方导航栏

- 全屏播放

- 演讲者模式

- 幻灯片列表

---
layout: section
---

# 语法介绍

---
layout: two-cols
---

# Markdown

<div />

幻灯片的内容使用 Markdown 语法编写

```md
# 标题

- 列表项 1
- 列表项 2

**粗体** *斜体* ~~删除线~~

[链接](https://sli.dev)
```

::right::

<div p-24>

# 标题

- 列表项 1
- 列表项 2

**粗体** *斜体* ~~删除线~~

[链接](https://sli.dev){.text-blue}

</div>

---

# 分隔幻灯片

```md
# 第一页

第一页的内容

---

# 第二页

第二页的内容
```

<div mt-8 op-80>

注：VSCode 拓展会使用蓝色线条突出分隔符

</div>

---

# 配置幻灯片

```md
---
theme: seriph
---

# 第一张幻灯片

---
layout: intro
---

# 第二页的布局是 intro！

---

# 第三页没有任何配置
```

<div v-click rounded-xl border="2 yellow" v-drag="[63,115,221,80]" />

<div v-after text-yellow v-drag="[301,108,363,NaN]">

第一页前的配置是 `Headmatter`

用于配置整个文稿的属性

</div>


<div v-click rounded-xl border="2 green" v-drag="[63,260,221,80]" />

<div v-after text-green v-drag="[301,253,363,NaN]">

其他每页前的配置是 `Frontmatter`

用于配置单页的属性

</div>

<div v-click rounded-xl border="2 red" v-drag="[61,400,223,44]" />

<div v-after text-red v-drag="[295,392,363,NaN]">

`Headmatter` 和 `Frontmatter` 都是可选的

</div>

---
layout: two-cols
---

# 代码块

<div />

朴实无华的代码块，语法和 Markdown 相同

````md
  ```js
  console.log('Hello, Slidev!')
  ```
````

<div v-click>

带有动态突出显示的代码块

````md
  ```js {1-2|3|4}
  const a = 2;
  const b = 3;
  const c = a ** b;
  console.log(c);
  ```
````

</div>

::right::

<div pt-24 pl-10>

```js
console.log('Hello, Slidev!')
```

</div>

<div v-click="1" pt-24 pl-10>

```js {1-2|3|4}
const a = 2;
const b = 3;
const c = a ** b;
console.log(c);
```

</div>

---

# 代码编辑器

# 交互式运行

---
layout: section
---

# 导出和部署

---

# 导出

```bash
npm run export --format pdf
npm run export --format pptx
npm run export --format png
```

---

# 部署

GitHub Pages

---
layout: section
---

# 一些技巧

---

# 同步

---

# AI

Bolt.new

Copilot

---

# 加入我们的社区

欢迎提 issue 和问题，也欢迎 PR

<carbon-logo-github /> **GitHub**: https://github.com/slidevjs/slidev <div h-2/>

<carbon-logo-discord /> **Discord**: https://chat.sli.dev <div h-2/>

<cib-tencent-qq /> **QQ Group**: 978643067

<img src="./assets/qqgroup.jpg" rounded-xl v-drag="[607,100,305,NaN]" />

---
layout: section
---

## 题外话

# TypeScript 开源社区

---

# 什么是开源

<div />

<v-clicks>

- 字面意思：开放源代码

- 做慈善？/ 另一种商业模式？/ 好玩？ / 刷履历？

- <span text-2xl> **开源是一种礼物** </span>

</v-clicks>

<div v-after>

<div v-drag="[478,201,480,311]">
<div text-blue>
https://talks.antfu.me/2024/vueconf-shenzhen/3
</div>
<h2>Yak Shaving <span op50 font-serif italic mb--1 text-26px> by Anthony Fu </span></h2>
<img src="./assets/yakshaving.png" rounded-lg shadow-xl w-120 border="~ gray/25" mt-1 />
</div>
</div>

---

# 开源世界里不同的社区

<div />

- Linux 为代表的社区和 TypeScript 社区
    - 有相似之处
    - 成员上几乎没有交集
    - 有很多不同

- TypeScript / JavaScript 的特性
    - 脚本语言，更加难闭源
    - 大多数代码用于编写 UI，没必要隐藏代码
    - Web 世界开放共享的文化
    - “顺手就开源了” / “开源了没坏处” （当然，公开代码 ≠ 维护项目）

---

# 我参与开源的一年

<div />

- 第一次使用 Slidev 是在初中，那时 Slidev 刚发布不久，非常火爆

- 今年二月提交了第一个 PR，随后加入了 Slidev 团队

- 修复 bug、添加功能、重构代码、回答社区里的问题

- 甚至修复了一个我初中就碰到的 bug（很有趣的经历）

- 为 Slidev 编写 VSCode 拓展时，想到去开发 reactive-vscode 这个库

- 以此为契机，结识了很多朋友，包括 Slidev 的作者 Anthony Fu

- 参加了 VueConf 2024，Rolldown 团队成员告诉我 “Rust 不难”

- 于是第三次入门 Rust，终于入门成功

---

# 一些信息

<div />

1. 开源是一种礼物。不要功利地看待，但坚信它对你的价值

2. 如果你想参与开源，JavaScript / TypeScript 社区是一个很好的起点

    - 门槛不高
    - 社区活跃
    - 华人参与度不错

3. 参与开源可能需要一个契机。从你的需求出发，找到一个你感兴趣的项目

---

# 其他感想

<div />

1. GitHub 上的星星数只能作相对比较，不能作绝对比较

2. 那面绿墙只能说明这位用户是否还在使用 GitHub

3. 使用英文和 minimal reproduction

---
layout: end
---

谢谢大家！
