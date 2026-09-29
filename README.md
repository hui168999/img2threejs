🌐 **简体中文** | [English](README_EN.md)

<div align="center">

<img src="assets/logo.svg" width="112" height="104" alt="img2threejs logo" />

# img2threejs

**把参考图片中的物体，重建成纯代码、程序化的 Three.js 模型。**

质量门控、开箱即可做动画、刻意省 token —— 用代码重建，而非摄影测量、网格抽取或下载现成素材包。

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-2.0.0-green.svg)](CHANGELOG.md)
[![PRs welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![Runtime](https://img.shields.io/badge/runtime-Three.js-000000.svg)](https://threejs.org)
[![Tooling](https://img.shields.io/badge/tooling-Python%203.10%2B%20stdlib-3776ab.svg)](forge)
[![Sponsor](https://img.shields.io/badge/Sponsor-Ko--fi-FF5E5B.svg?logo=kofi&logoColor=white)](https://ko-fi.com/iamnick)
[![Scripts](https://img.shields.io/badge/scripts-forge%20%2F%20scripts-3776ab.svg)](scripts)
[![Sponsored by Atlas Cloud](https://img.shields.io/badge/Sponsored%20by-Atlas%20Cloud-000000.svg?labelColor=1a1a1a&logo=data:image/svg%2Bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA4NDUuOTUgNzkyIj48cGF0aCBmaWxsPSIjZmZmIiBkPSJNNzEyLjA1LDU5NC4zTDQyMi45OCwxNS40NiwxMzMuOSw1OTQuM2wtOTEuMDEsMTgyLjI1YzU3LjE4LTM0LjU1LDExOS40OS02MS40LDE4NS40NC03OS40NSw2Mi4wMi0xNi45NywxMjcuMjQtMjYuMjEsMTk0LjY1LTI2LjIxLDM0LjY5LDAsNjguNzksMi40OSwxMDIuMTksNy4xOGwtNjUuNzItMTQxLjc2Yy0xOC42MS0zLjIzLTEwMS4yOC0zLjIzLTE2MS44Myw5Ljg0bDEyNS4zNi0yNzMuMTYsMTk0LjY1LDQyNC4xMmMuMzUuMS42OS4yMSwxLjAzLjMsNjUuNTcsMTguMDQsMTI3LjUzLDQ0Ljc4LDE4NC40MSw3OS4xNGwtOTEuMDEtMTgyLjI1WiIvPjwvc3ZnPg%3D%3D)](https://www.atlascloud.ai/console/coding-plan)
[![Sponsored by Tripo](https://img.shields.io/badge/Sponsored%20by-Tripo-000000.svg?labelColor=1a1a1a&logo=data:image/svg%2Bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbC1ydWxlPSJldmVub2RkIj48cGF0aCBmaWxsPSIjZmFjZTAwIiBkPSJNMTIuNjYxIDQuNzUyYS4wNC4wNCAwIDAwLS4wMTMtLjA1NS4wMzguMDM4IDAgMDAtLjAyLS4wMDVINi40OTZhLjE5LjE5IDAgMDEtLjE2NS0uMDkyTDQuMjQ1IDEuMDUyYS4wMzQuMDM0IDAgMDEuMDE0LS4wNDdBLjAzOC4wMzggMCAwMTQuMjc1IDFjNS40OTIgMCAxMC43MzMgMCAxNS43MjEuMDAyIDIuMDg5IDAgMy42OTkgMS41NCA0LjAwMyAzLjU5OC4wMDguMDYyLS4wMTkuMDkyLS4wOC4wOTJoLTYuNjdhLjIwNC4yMDQgMCAwMC0uMTc0LjFjLTEuNDE0IDIuNDEtMi44MiA0LjgwMy00LjIxOCA3LjE3OC0uMjguNDcyLS45Mi42Mi0xLjM3My4zNDItLjE5LS4xMTYtLjM1Ny0uMzA0LS41MDItLjU2MWEzNy45MTcgMzcuOTE3IDAgMDAtLjg4Mi0xLjQ4OWMtLjIyMi0uMzU2LS4yMzQtLjcwNy0uMDM1LTEuMDUyYTY2MS43NyA2NjEuNzcgMCAwMTIuNTk3LTQuNDZ2LjAwMnoiLz48cGF0aCBmaWxsPSIjZmZmIiBkPSJNMTAuNzcyIDE2Ljk4NmMuNTcuOTcyIDEuOTM1LjkxNiAyLjQ4OS0uMDI4TDE5IDcuMTY0YS4xMjcuMTI3IDAgMDEuMTE2LS4wNjdoNC4yM2MuMDE3IDAgLjAzLjAxNC4wMjguMDMgMCAuMDA1LS4wMDEuMDEtLjAwMy4wMTMtMi42MDUgNC40MzItNS4yMzIgOC45MDYtNy44OCAxMy40Mi0xLjI4MyAyLjE5MS00LjI3OCAyLjUxNy02LjE3OS45NDctLjMwOC0uMjU0LS42NjUtLjcyNy0xLjA2OS0xLjQxNy0yLjUyNS00LjMyNC01LjA5OC04LjcxLTcuNzItMTMuMTYyLTEuMDYzLTEuODAzLS40MjQtMy45NDcgMS4xOS01LjIuMDUzLS4wNDEuMDk1LS4wMzMuMTI5LjAyMyAyLjkwNSA0Ljk1IDUuODgyIDEwLjAyOSA4LjkzIDE1LjIzNnoiLz48L3N2Zz4%3D)](https://www.tripo3d.ai/)
[![Sponsored by Hyper3D](https://img.shields.io/badge/Sponsored%20by-Hyper3D-000000.svg?labelColor=1a1a1a&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAAAXNSR0IArs4c6QAAAERlWElmTU0AKgAAAAgAAYdpAAQAAAABAAAAGgAAAAAAA6ABAAMAAAABAAEAAKACAAQAAAABAAAAIKADAAQAAAABAAAAIAAAAACshmLzAAADlElEQVRYCeWWbWiOURjH9wzDZoYs5i3aF%2FEBiTYZRQ35qGxS%2B2AoFNoHRcl7vlETGcWX1aLkLbKsJTNiXmpKpExt5v2lGWNte%2Fz%2Bd%2Ff9dO6z57mfe08p5arfc851netc57rP23PS0v53iYSZgGg0Ogy%2F5VACU%2BAnnIlEIjWUf1cYvAgaIZ7sxxjqI1LKkuCb4Ue8kV1bB%2BXElIIn60TgLdDnDhRULEsWa8DtjKZp7woa1W37TTljwAMEdSBgFjS5AyQrzuOQ7jKCcnBQ7FBtBCmHZPIdh0oYpaCUObATnoCS3wPzwwzo28F0GkKnezDX7fyJ8gF8hT54Bc3wmCP4mtIn9C%2FCcBbyoQv2QSW%2BqicXAhRAL7yFU3AI6uEoTE8ewZmNqfg%2BB8kL0FFdEqavpnI9qPNe0HRKdkOGHQBbBIbbdunYi6EbfsER%2BAC6yBILDgqoo3cavBOwPXEPZyDNWNxjiP0iSA6CTks7zAyKp8xLwBv8ZKCz24j%2FMVhj%2B2JbCRItoy4syW0YavvGdBovywvRHpgcawio4LcBWmG06YaeB7pFlUAneFJm%2BqWbCvWXrn6FndtqtSVSJ9GgPTLecviG3gDZYH71VjLRn5sjdgKNrv2CWwYWBNItOBZqYZ7l3IN%2BHyaAeUHNQS8AR8wGGe6AvlznP64w6FIaRrosoNTAs6AOTNGXt8Em00hdH10It8CXWRrT%2FpEBTmA3p0x%2BppSj2JtOF403e56vlmA25HoGo1TijtgzIONxiK2R4%2BX%2F6fWrjnaO3xbLnoduJ%2Bq55HgVew%2FIHoUMZiLTc7JKe3Y09TuYPV3VpixE8Z0Ms9Grx2aAAZWMprcCpsEzbFUErqJuyk0Ubbz3oMFr8NETzZagS6fddtYltBbiyeF%2BziEMBCqNF8y1lfpCYNQ1fDegw0batPNDCb6ZkAstYMsjDP6lwaA1b7Y9DV033S5YB1mJsqAtGyrAeSVRFkIj6CbUdVwH%2BWb%2F2HuAhus0rDAbrXotus61LhKt%2FTX4DBLNjv7tVkE9bGNfaDNrabW3dBx74Klnp%2B4XHBeD%2FrWCpJpGvRNMP%2FPh%2BoC20EvlzwCNzmVg%2FnGg9pOHWA7AJdDSeHKVyoCf6LEl8LIhiN5yekoVQ7x7Qq468w2gP68meAc3mN5uygFJvwS83iSyiPpqUELjYAwooU7QgG%2BgGjTwF8qUJGECZjSS0bWqy2cQdEBbKl9Lv39P%2FgAQ2ul5m76dAQAAAABJRU5ErkJggg%3D%3D)](https://hyper3d.ai/)

<table align="center">
  <tr>
    <td align="center"></td>
    <td align="center"><sub><b>DAILY</b></sub></td>
    <td align="center"><sub><b>WEEKLY</b></sub></td>
  </tr>
  <tr>
    <td align="right"><sub><b>Python</b></sub></td>
    <td><a href="https://trendshift.io/repositories/83608?utm_source=trendshift-badge&amp;utm_medium=badge&amp;utm_campaign=badge-trendshift-83608" target="_blank" rel="noopener noreferrer"><img src="https://trendshift.io/api/badge/trendshift/repositories/83608/daily?language=Python" alt="hoainho%2Fimg2threejs | Trendshift" width="250" height="55"/></a></td>
    <td><a href="https://trendshift.io/repositories/83608?utm_source=trendshift-badge&amp;utm_medium=badge&amp;utm_campaign=badge-trendshift-83608" target="_blank" rel="noopener noreferrer"><img src="https://trendshift.io/api/badge/trendshift/repositories/83608/weekly?language=Python" alt="img2threejs%2Fimg2threejs | Trendshift" width="250" height="55"/></a></td>
  </tr>
  <tr>
    <td align="right"><sub><b>All languages</b></sub></td>
    <td><a href="https://trendshift.io/repositories/83608?utm_source=trendshift-badge&amp;utm_medium=badge&amp;utm_campaign=badge-trendshift-83608" target="_blank" rel="noopener noreferrer"><img src="https://trendshift.io/api/badge/trendshift/repositories/83608/daily" alt="img2threejs%2Fimg2threejs | Trendshift" width="250" height="55"/></a></td>
    <td><a href="https://trendshift.io/repositories/83608?utm_source=trendshift-badge&amp;utm_medium=badge&amp;utm_campaign=badge-trendshift-83608" target="_blank" rel="noopener noreferrer"><img src="https://trendshift.io/api/badge/trendshift/repositories/83608/weekly" alt="img2threejs%2Fimg2threejs | Trendshift" width="250" height="55"/></a></td>
  </tr>
</table>

</div>

*参考图片被用代码重建成可在浏览器中实时运行、支持动画的 Three.js 模型。*

### [→ 打开在线演示画廊](https://img2threejs.io/)

画廊里的每个模型都是生成的代码，直接在你的浏览器中运行。没有网格文件，无需下载。

---

## 在线演示

全部由基本几何体、程序化着色器和生成的几何体重建而成。打开任意模型可以旋转查看、核对参考图、阅读生成的源码。

| 演示 | 类型 | 构建版本 | 预览 | 源码 |
| --- | --- | --- | --- | --- |
| Dual-Sword Warrior — TypeScript procedural surfaces ⚠︎ | 角色 | `v1.5.1` | [在线](https://img2threejs.io/#/demo/girl-character) | [代码](https://github.com/img2threejs/img2threejs-showcase/blob/main/src/demos/girl-character/createGirlCharacterModel.ts) |
| Low-Poly Humanoid — Rigged Character ⚠︎ | 角色 | `v1.5.0` | [在线](https://img2threejs.io/#/demo/low-poly-humanoid) | [代码](https://github.com/img2threejs/img2threejs-showcase/blob/main/src/demos/low-poly-humanoid/createLowPolyHumanoidModel.ts) |
| ★ Talon Knife \| Doppler Ruby (Factory New) | 物体 | `v1.4.4` | [在线](https://img2threejs.io/#/demo/talon-doppler-ruby) | [代码](https://github.com/img2threejs/img2threejs-showcase/blob/main/src/demos/talon-doppler-ruby/createTalonDopplerRubyModel.ts) |
| AWP \| Medusa (Minimal Wear) · V2 rebuild | 物体 | `V2` | [在线](https://img2threejs.io/#/demo/awp-medusa-v2) | [代码](https://github.com/img2threejs/img2threejs-showcase/blob/main/src/demos/awp-medusa-v2/createAwpMedusaModelV2.ts) |
| Pikachu 10K Star Celebration ⚠︎ | 角色 | `v1.5-beta` | [在线](https://img2threejs.io/#/demo/electric-mouse-mascot) | [代码](https://github.com/img2threejs/img2threejs-showcase/blob/main/src/demos/electric-mouse-mascot/createElectricMouseMascotModel.ts) |
| Glock-18 \| Ghost Protocol (Well-Worn) | 物体 | `v1.4.1` | [在线](https://img2threejs.io/#/demo/glock-ghost-protocol) | [代码](https://github.com/img2threejs/img2threejs-showcase/blob/main/src/demos/glock-ghost-protocol/createGlockGhostProtocolModel.ts) |
| Classic Knife \| Fade (Minimal Wear) | 物体 | `v1.3` | [在线](https://img2threejs.io/#/demo/classic-fade) | [代码](https://github.com/img2threejs/img2threejs-showcase/blob/main/src/demos/classic-fade/createClassicFadeModel.ts) |
| BMX Endurance Bike | 物体 | `v1.3` | [在线](https://img2threejs.io/#/demo/bmx-endurance) | [代码](https://github.com/img2threejs/img2threejs-showcase/blob/main/src/demos/bmx-endurance/createBmxEnduranceBikeModel.ts) |
| M9 Bayonet \| Doppler Phase 2 | 物体 | `v1.3` | [在线](https://img2threejs.io/#/demo/m9-doppler) | [代码](https://github.com/img2threejs/img2threejs-showcase/blob/main/src/demos/m9-doppler/createM9DopplerModel.ts) |
| Sony WF-1000XM3 Earbuds + Case | 物体 | `v1.2` | [在线](https://img2threejs.io/#/demo/sony-wf1000xm3) | [代码](https://github.com/img2threejs/img2threejs-showcase/blob/main/src/demos/sony-wf1000xm3/createSonyWf1000xm3Model.ts) |
| ISSACA 12 Gauge Shotgun | 物体 | `v1.2` | [在线](https://img2threejs.io/#/demo/issaca-shotgun) | [代码](https://github.com/img2threejs/img2threejs-showcase/blob/main/src/demos/issaca-shotgun/createIssacaShotgunModel.ts) |
| Gerber Paracord Knife | 物体 | `v1.2` | [在线](https://img2threejs.io/#/demo/gerber-knife) | [代码](https://github.com/img2threejs/img2threejs-showcase/blob/main/src/demos/gerber-knife/createGerberKnifeModel.ts) |
| Doraemon House (isometric diorama) | 物体 | `v1.2` | [在线](https://img2threejs.io/#/demo/doraemon-house) | [代码](https://github.com/img2threejs/img2threejs-showcase/blob/main/src/demos/doraemon-house/createDoraemonHouseModel.ts) |
| War-Hauler "SECTOR 07" | 物体 | `v1.2` | [在线](https://img2threejs.io/#/demo/warhauler) | [代码](https://github.com/img2threejs/img2threejs-showcase/blob/main/src/demos/warhauler/createWarHaulerModel.ts) |
| Crowned Loot Chest ⚠︎ | 物体 | `v1.2` | [在线](https://img2threejs.io/#/demo/crown-chest) | [代码](https://github.com/img2threejs/img2threejs-showcase/blob/main/src/demos/crown-chest/createCrownChestModel.ts) |

⚠︎ 标记表示该演示在注册表中的 `status` 仍为 `placeholder` 而非 `final` —— 可以渲染，但还不是完成品。**构建版本**一列记录的是每个演示自身注册表项中 `generatedWith` 的版本，而非按日期推断；`awp-medusa-v2` 记录的 `V2` 是该演示的重建轮次，而非 release 号。行按加入演示的 commit 时间倒序排列。

画廊源码位于 [img2threejs/img2threejs-showcase](https://github.com/img2threejs/img2threejs-showcase)。如果这个项目对你有用，点个 star 能帮更多人发现它。

---

## 它能做什么

给你一张物体的参考图，它会产出一个 TypeScript 编写的 `THREE.Group` 工厂函数，用基本几何体、程序化着色器和生成的几何体重建这个物体 —— 自带运行时层级结构（轴心点、插槽、碰撞体），结果开箱即可做动画，而不是一团死模型。

它运行在 Claude Code、Codex 或 OpenCode 之下，与 agent 无关：文档里凡是写"agent 视觉"或"agent 浏览器工具"的地方，都会用宿主提供的能力 —— 原生图片读取、浏览器 MCP、项目预览，或用户提供的截图。

### 支持对象与细节精度

- **物体与角色。** 每个对象会被分类为 `object`（物体）、`character`（角色）或 `hybrid`（混合）。物体走硬表面管线；角色走解剖学感知流程（头身比例、面部关键点、姿态），详见 `grimoire/character/reconstruction.md`。
- **细节优先分析。** 生成代码之前，管线会先枚举一份 `detailInventory`：决定这个东西"长得像"的细小特征（光泽、倒角/圆角、螺丝/铆钉、雕刻或喷绘线条、轮廓、污渍与磨损）。每个细节必须映射到真实部件或材质条目，严格的质量门控会在清单完整之前阻止生成。分类法见 `grimoire/intake/detail_inventory.md`。
- **特定人物/角色的最大相似度。** 可选的投影优先路径会把参数化模板拟合到图像关键点、对照片去光照、做相机匹配渲染，再把参考图投影到网格上。单张图无法保证 100% 相像，因此管线会报告每个区域的置信度，关键时候会要求提供更多视角。详见 `grimoire/character/likeness_maximization.md`。
- **多视角剪影雕刻。** 可选的 `geometryDescriptor.visualHull` 会把至少两个确定性正交二值剪影相交成有界、焊接的体素网格。看不到的区域记为低置信度，而不是编造隐藏细节。结构与运行时检查见 `grimoire/scripts.md`。
- **CS2 武器评审门控。** 刀和 Glock-18 路线使用家族专属部件契约。评审记录精确度等级、家族身份、喷绘区域与投影覆盖率、分区置信度、近似说明、版本化的评审场景元数据；部件覆盖率门控和去贴图白模门控防止"一张像的贴图代替真实结构"蒙混过关。随 CS2 领域插件发布，见其 `docs/cs2/review-gates.md`。
- **可续跑的本地工作流。** `forge/state.py` 为通用 profile 和每个已注册领域（内置 `character`，以及通过插件安装的 CS2、`animated-character` 等）记录有序、有证据的 intake/pass 检查清单。`forge/next.py --state` 可从清单断点续跑，已有的 spec、渲染与评审门控依然权威。
- **材质参考管线。** 每个可见材质区域都可以裁剪、分析、对照版本化的 Three.js 材质注册表解析、装配进 `ObjectSculptSpec`、从受控相机视角渲染，只有通过分区对比门控才算过关。见 [`docs/materials/README.md`](docs/materials/README.md)。
- **Python 辅助的浏览器渲染。** Python 可以编排相机批量任务、哈希、清单和确定性诊断，但目标浏览器 Three.js 路线始终是渲染的权威。见 [`grimoire/build/python_threejs_render_bridge.md`](grimoire/build/python_threejs_render_bridge.md)。

---

## 工作原理

分阶段雕刻管线先把参考图变成 spec，然后逐个构建轮次生成并做视觉评审 —— `blockout → structural → form → material → surface → lighting → interaction → optimization` —— 自我修正，直到每个决定性特征都达到阈值。

**→ 完整管线图、门控、自我修正逻辑与省 token 设计：[docs/ARCHITECTURE.md](docs/ARCHITECTURE.md)**
分阶段雕刻管线先把参考图变成 spec，然后逐个构建轮次生成并做视觉评审 —— `blockout → structural → form → material → surface → lighting → interaction → optimization` —— 自我修正，直到每个决定性特征都达到阈值。确定性 Python 脚本负责校验与门控；模型 token 只花在视觉判断和代码上。

**→ 完整管线图、门控、自我修正逻辑、脚本索引与省 token 设计：[docs/ARCHITECTURE.md](docs/ARCHITECTURE.md)**

---

## 快速上手

1. **安装** —— 把这个文件夹放进你的 skills 目录：

   ```bash
   git clone https://github.com/img2threejs/img2threejs.git ~/.claude/skills/img2threejs
   ```

   如果你用多个宿主，保留一份 checkout，各入口用软链接指向它，避免版本漂移：

   ```text
   ~/.claude/skills/img2threejs -> <你的 checkout 路径>
   ~/.codex/skills/img2threejs  -> <你的 checkout 路径>
   ```

2. **添加领域插件（可选）** —— 领域知识（目前是 CS2 皮肤）放在已安装的插件里，不在这个 checkout 中。先安装一次 [img2 harness](https://github.com/img2threejs/img2)，再添加插件：

   ```bash
   npx github:img2threejs/img2 install   # ~/.img2、插件注册表和 `img2` 启动器
   img2 add img2threejs/plugin-cs2       # 按最新 tag 克隆、锁定 SHA、链接宿主 skills
   img2 doctor                           # 对所有已装插件做 fail-loud 静态审计
   ```

   已安装的领域插件会贡献自己的检查清单步骤、证据采集、spec 增强（质量下限只升不降合并）、阻塞式评审门控，并用 `forge/state.py init --profile <id>` 注册自己的 profile。不装插件时可用 `generic` 和 `character`；缺插件的 profile（`cs2`、`animated-character`）会大声报错说明装了什么，绝不静默降级。`img2 remove <id>` 可干净卸载。

   **官方插件：**

   | 插件 | 提供 | 安装 |
   |---|---|---|
   | [plugin-cs2](https://github.com/img2threejs/plugin-cs2) | `cs2` profile —— CS2 武器皮肤重建：家族适配器、涂装规则、领域评审门控 | `img2 add img2threejs/plugin-cs2` |
   | [plugin-character](https://github.com/img2threejs/plugin-character) | `animated-character` profile —— `character` 的全部能力，外加 Stage R 骨骼/动画门控 | `img2 add img2threejs/plugin-character` |
   | [plugin-img2glb](https://github.com/img2threejs/plugin-img2glb) | 经由托管 TRELLIS space 的 `image → glb` 输出目标 | `img2 add img2threejs/plugin-img2glb` |
   | [plugin-hello-cube](https://github.com/img2threejs/plugin-hello-cube) | 最小参考插件 —— 照着它写你自己的 | `img2 add img2threejs/plugin-hello-cube` |

   自己写插件：看 harness 仓库的 [docs/WRITING_A_PLUGIN.md](https://github.com/img2threejs/img2/blob/main/docs/WRITING_A_PLUGIN.md)。

3. **调用** —— 在 Claude Code 里附上或指向一张物体图片，运行：

   ```
   /img2threejs 把这个物体重建成 Three.js 模型，保持比例、角度和颜色。
   ```

   一行就够：skill 会自己分类对象、跑细节清单、每一轮都过门控。

4. **跟着管线走** —— skill 会校验图片、写评估与 spec、逐轮生成工厂函数，每一步都给你并排对比图，直到渲染与参考图对上。

   多会话重建时，先建一个本地状态索引：

   ```bash
   python3 forge/state.py init --reference <图片> --profile character --spec object-sculpt-spec.json
   python3 forge/next.py --state .img2threejs/state.json
   ```

### 进阶用法

上面的一行调用把判断都交给了 skill。当你已经清楚"正确"对你的对象意味着什么，直接说出来 —— 下面每行都对应管线里真实存在的门控或产物，所以它们改变的是实际执行的标准，而不只是加形容词：

```
/img2threejs 把这张图里的对象重建成程序化 Three.js 模型。

保真度  比例与剪影以参考图为准。先枚举决定性细节 —— 倒角与圆角、
        板块接缝、紧固件、雕刻或喷绘线条、光泽/哑光分区、磨损 ——
        放不到真实部件上的细节直接丢掉，不许造假。
材质    涂装类别与渐变色阶从参考图像素推导，不许凭记忆。
        经不起 tone-mapping 的颜色要标出来。
运行时  该动的地方暴露轴心点和插槽，再加一个 userData.tick 做循环待机动画。
门控    跑 --strict-quality，并排评审没通过就不进入下一轮。
        图片看不到的区域，逐区报告置信度。
```

按对象类型可加的：

- **特定人物或角色** —— `最大化相似度：把参数化模板拟合到关键点，对参考图去光照、做相机匹配，然后投影。告诉我哪些区域是推断的。`
- **动物** —— `这是生物不是人形 —— 用四足身体方案和 body-unit 比例系统。`
- **高饱和阳极氧化/糖果漆** —— `这是糖果漆涂层，不是宝石金属。保住色相，别让环境光偷走它。`
- **成本上限** —— `保持 low effort，跳过展示用 composer；我只要评估渲染图。`

脚本在 skill 根目录运行，只需要 Python 3.10+ —— 零安装。

```bash
python3 forge/stage1_intake/probe_image.py <image>
python3 forge/stage2_spec/new_pre_spec_assessment.py "名称" --image <image> --out assessment.json
python3 forge/stage2_spec/new_sculpt_spec.py "名称" --image <image> --assessment assessment.json --out spec.json
python3 forge/stage2_spec/validate_sculpt_spec.py spec.json --strict-quality
python3 forge/stage3_build/generate_threejs_factory.py spec.json --out src/createObjectModel.ts
```

工厂生成器会重复执行 strict-quality 门控，采用 fail-closed：失败时返回 `BLOCKED` 并附带 spec 产物、失败指标、原因和下一步动作，不写工厂文件。`--allow-nonstrict` 仅用于显式声明的 legacy 测试 fixture，绝不用于正式输出。

### GLB 参考路线的复制粘贴提示词

用 **GLB 参考**而非照片重建角色是另一条路线，有自己的门控 —— GLB 只是测量仪器，永远不会发布。三个提示词各管一块：

| 提示词 | 适用 | 不适用 |
|---|---|---|
| [构建](docs/GLB_CHARACTER_PROMPT.md) | 有 GLB 但还没建出表面 | 没有 GLB，或构建已完成只是看着不对 |
| [打磨](docs/GLB_CHARACTER_POLISH_PROMPT.md) | 构建已完成但结果不像 GLB | 表面根本没建出来 —— 那是重跑构建，不是打磨 |
| [动画](docs/GLB_CHARACTER_ANIMATION_PROMPT.md) | 静止看着对了且已过构建门控 | 表面没过门控，或 `joint_loops.py` 失败 —— 那是表面问题，调权重解决不了 |

它们强制把 GLB 真正携带的每个参数 —— 尺寸、比例、每段宽度与质心、基础色、粗糙度与金属度 —— 推到测量值，并附带证明落地的检查。三样东西**不是** 1:1，每个提示词都写明了：绑定与动画通常不在资产里（`skinCount: 0`、`animationCount: 0`），纹理图和法线贴图按本 skill 纯代码约定故意不复制，小于节点单元尺寸的细节根本带不过来。

**这些是参考资料，不是保证。** 它们写得通用，里面的测量数字来自某一个角色，是用来示范"量什么"的 —— 不是让你照抄的值。按你的情况跑对的那一个，别三个连着跑；每个都注明了用错顺序的代价。

脚本逐个说明、完整脚本表与预期产物，见 [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md)。

---

## 为什么省 token

多数图生 3D 的 agent 循环把 token 烧在让模型干机械活上 —— 每轮重读整个模型、逐像素打分、手工校验 JSON、重跑做过的步骤。img2threejs 把这些全推进确定性脚本，模型 token 只花在真正需要判断的地方。

- **脚本执行，模型判断。** Python 脚本负责校验、门控、spec 编写、PBR 提取、对比图打包、管线状态。它们从不评价视觉。模型的 token 只干一件事：看一张并排对比图，判定通过还是不通过。
- **零依赖，零安装折腾。** 所有脚本都是纯 Python 3.10+ 标准库。不用 pip，不用 PIL、numpy、Playwright。PNG 读写用 `struct` 和 `zlib` 手写。没东西可装，就没东西可在上下文里调。
- **按轮次门控生成。** 代码生成器每次只输出当前解锁的构建轮次。模型不用每轮重生成、重读整个模型 —— 每步都小而聚焦。
- **尽早失败，在写代码之前。** strict-quality 门控在生成一行 Three.js 之前就拦下肤浅的 spec，绝不把 token 烧在从一开始就欠 spec 的模型渲染上。
- **每轮只看一张图。** 每轮只用一张打包好的对比图（参考图并排渲染图）评审，不用一堆零散截图。
- **文本输出，不是二进制。** 结果是可 diff 的 TypeScript 加 JSON spec —— 小、可审、可进版本控制，而不是几 MB 的网格文件。

净效果：同样从一张图得到保真的 3D 模型，但昂贵的模型上下文只留给视觉判断和代码，不浪费在记账上。分阶段、分轮次的完整 token 拆解见 [docs/TOKEN_COST.md](docs/TOKEN_COST.md)。

---

## 脚本一览

| 脚本 | 作用 |
| --- | --- |
| `stage1_intake/probe_image.py` | 图片元数据与明显技术问题（不是视觉检查）。 |
| `stage2_spec/new_pre_spec_assessment.py` | 给物体分类、评复杂度、输出质量契约。 |
| `stage2_spec/new_sculpt_spec.py` | 从评估编写 ObjectSculptSpec。 |
| `stage2_spec/validate_sculpt_spec.py` | 校验 spec；`--strict-quality` 在写代码前拦下肤浅 spec。 |
| `stage1_intake/extract_pbr_evidence.py` | 按裁剪区提取参考图派生的 PBR 证据（推断，非逆向渲染）。 |
| `stage1_intake/material_region_analysis.py` | 裁剪材质区域，跑纹理/PBR 证据，解析注册表 profile。 |
| `stage2_spec/apply_material_analysis.py` | 把区域分配、先验、贴图与出处写进 ObjectSculptSpec。 |
| `stage3_build/orchestrate_passes.py` | 锁定的轮次状态：status、check、sync。 |
| `stage3_build/generate_threejs_factory.py` | 为当前解锁轮次输出 Three.js `Group` 工厂。 |
| `stage4_review/material_views.py` | 输出多角度、放大、显微镜、环境与捕获回读契约。 |
| `stage4_review/material_comparator.py` | 对比可见材质裁剪区，按通道归类不匹配。 |
| `stage4_review/material_feedback.py` | 在现有停止策略内做有界、材质范围的修正。 |
| `stage4_review/material_gate.py` | 注册表、裁剪区、渲染、兼容性、对比证据全过才放行材质轮次。 |
| `stage4_review/make_comparison_sheet.py` | 打包一张参考图 vs 渲染图的评审图。 |
| `stage4_review/append_review.py` | 记录每轮评审：分数、结论、证据。 |
| `_shared/feature_acceptance_policy.py` | 内部 helper，执行按特征的分数阈值。 |
| `stage1_intake/build_detail_inventory.py` | 把参考图分区，搭细节清单脚手架。 |
| `stage1_intake/extract_landmarks.py` | 叠加关键点网格，给角色搭解剖块脚手架。 |
| `stage1_intake/solve_camera_pose.py` | 输出参考相机位块，让渲染可以做相机匹配。 |
| `stage1_intake/delight_albedo.py` | 从照片近似中性反照率，供纹理投影前用。 |
| `stage3_build/bake_projected_texture.py` | 输出照片纹理投影的投影/UV 烘焙描述符。 |

| `stage5_rig/rig_spec.py` | 从部件树派生并校验骨骼，骨头不能漂出几何体。 |
| `stage5_rig/geodesic_skinning.py` | 沿实体内部距离算顶点权重；刚性部件不进平滑蒙皮。 |
| `stage5_rig/validate_rig_payload.py` | 绑定 `THREE.Skeleton` 前的阻塞式载荷完整性门控。 |
| `stage1_intake/extract_hair_evidence.py` | 发肤分离、分区覆盖率、发际线、高光带、发根到发梢差值。 |
| `stage4_review/scalp_exposure.py` | HARD 门控：在渲染前找出几何体上的秃斑。 |
| `stage4_review/hair_gate.py` | 软门控：头发覆盖率、发际线与高光偏移对照参考图。 |
| `stage4_review/interior_difference.py` | 剪影内部的外观差异，按高度分区。每轮视觉必跑。 |
| `_shared/chirality.py` | 左右手性作为可导入约定，附带两种手性缺陷各自需要的门控。 |
| `_shared/pipeline_routing.py` | fail-closed 的武器/角色路由；低置信度走 `request-input`。 |

以上是精选 —— `forge/` 下约有九十个模块。可执行索引与每个 flag 见 [`grimoire/scripts.md`](grimoire/scripts.md)，逐门控契约见 [`grimoire/review/gates_reference.md`](grimoire/review/gates_reference.md)。`grimoire/` 其余部分是各门控用的评分细则（校验、预 spec 评估、程序化模式、材质与光照真实感、附件正确性、可动模型、自我修正）。

### 可选的参考保真工具

stdlib 核心可以在不引入运行时依赖的前提下使用隔离的证据层：
SAM2 部件掩膜、Depth Anything V2 相对深度先验、MediaPipe 面部/姿态关键点、
Chrome DevTools 诊断、Three.js 场景检查、Playwright 跨浏览器兜底、版本感知的 Context7 检索。这些工具从不批准某个轮次，也不静默提供几何体。安装、路由、出处规则与确切命令见 [`docs/integrations/reference_fidelity_tooling.md`](docs/integrations/reference_fidelity_tooling.md)。

### 可选的 GLB 基准角色管线

[`integrations/glb_character_pipeline`](integrations/glb_character_pipeline) 用**多部件 GLB 做测量仪器加其漫反射图**重建角色，输出演示实际发布的程序化 TypeScript —— 运行时不拉取任何 `.glb` 或 `.bin`。它自带 `pyproject.toml`/`uv.lock`，让 stdlib 的 `forge` 核心保持零依赖，通过 `IMG2THREEJS_SHOWCASE_ROOT` 操作配套的 showcase checkout。

只在构建有 GLB 可测时用 —— 其他情况完全跳过，走核心的图片驱动管线。精确复现 `girl-character` 发布的 `crossSections.ts`（748 环、86,240 环点）。方法与分阶段理由见 [`PIPELINE.md`](integrations/glb_character_pipeline/PIPELINE.md)。

---

## 你能得到什么

- 一份 `ObjectSculptSpec` JSON：完整部件树、材质、重复系统、插槽，以及每轮的评审历史记录。
- 一个 TypeScript `createObjectNameModel(spec, options)` 工厂，返回 `THREE.Group`，`root.userData.sculptRuntime` 暴露节点、插槽、碰撞体与销毁组。
- 角色构建还有 `root.userData.rig`：骨骼、共享的单个 `Skeleton`、骨骼顺序与索引映射，以及根据每个蒙皮网格是否真实绑定算出的 `bound` 标志。
- 渲染图与对比图，记录每轮的保真度。
脚本逐个说明与完整输出产物列表，见 [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md)。

---

## 路线图

**已发布：**

- **v1.0** —— 物体管线：分阶段雕刻、渲染 vs 参考评审循环、可动层级。
- **v1.1** —— 细节优先分析：强制细节清单、strict-quality 门控。
- **v1.2** —— 人形角色生成器：解剖流程、比例锁定与特征定位轮次。
- **v1.3** —— 质量与效率：Divine Eye 确定性评审 harness、输入完整性门控与几何真实门控、参考图 grounding 的纹理与渐变分析、CIEDE2000 色彩数学。
- **v1.4 —— 武器更新** —— CS2 图像匹配重建：出处感知 intake、投影优先涂装、家族专属武器适配器、结构评审门控。
- **v1.4.1** —— CS2 加固：显式部件覆盖率、专用 Glock-18 装配契约、去贴图白模证据、更严的几何完整性检查。
- **生物生成器** —— 4 种身体方案（四足 / 鸟类 / 翼龙 / 蛇形）、`animalAnatomy` spec、脊柱放样几何、ΔE00 色彩门控。
- **v1.5 —— 角色更新** —— 从部件树派生骨骼并绑定到 `SkinnedMesh` 几何、测地线蒙皮、头发作为五阶段子系统（硬性的头皮暴露门控）、手性门控、内部差异评审、`tapered-sweep` 图元、带阻塞验收门控的材质管线、可续跑工作流状态。不含：`hairProfile` 编译器、IK、姿态扫描门控、服装。
- **v2.0 —— 插件更新** —— 领域注册表、拉式 spec 增强（质量下限只升不降）、带出处的输出目标插槽、按插件的阻塞门控、img2 harness（`img2 install/add/doctor`）。CS2 抽成 `plugin-cs2`，`animated-character` 由 `plugin-character` 提供；基础不再带领域。"插件生态与 API"原属 Procedural World 包，提前作为独立大版本发布。

**下一步 —— 每个版本一个主题：**
- **v2.1 —— 角色拆分**：内置 `character` 领域并入 `plugin-character`，基础不再带领域，v2.0 的插件拆分收官。
- **v2.2 —— 环境更新**：建筑、房间、街道、植被、地形感知与多物体重建。
- **v2.3 —— 游戏管线更新**：Unity 与 Unreal 导出器、Blender 桥、LOD 与碰撞网格生成。
- **v2.4 —— 动画更新**：自动骨骼、自动权重、Mixamo 兼容、面部骨骼。
- **v2.5 —— AI Studio 更新**：Web UI、批量处理、可视化提示词构建器、云渲染。
- **v3.0 —— 程序化世界更新**：多视角重建、程序化城市生成、语义世界理解。

主线：资产（v1.4–v1.5）→ 插件生态（v2.0–v2.1）→ 世界（v2.2–v2.3）→ 生产（v2.4–v2.5）→ 从参考图生成可玩世界的 AI 游戏资产平台（v3.0）。

**→ 完整路线图** —— 按版本详述、四阶段长视角、已跟踪的能力缺口：**[ROADMAP.md](ROADMAP.md)**。技术规格：[docs/UPGRADE_PLAN.md](docs/UPGRADE_PLAN.md)。

---

## 关于局限性的实话

单张图看不到背面，也保证不了精确几何。输出是近似、风格化或低多边形时 skill 会直说；看不到的面用镜像可见面推断，不会假装有把握。它擅长硬表面物体；角色是风格化重建，不是照片级相似。"这张图达不到你想要的保真度"是合法且符合预期的结果。

---

## Star 趋势

如果 img2threejs 对你有用，点个 star 能帮更多人发现它。

<a href="https://www.star-history.com/#hoainho/img2threejs&Timeline">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/chart?repos=hoainho/img2threejs&type=timeline&theme=dark&legend=top-left&sealed_token=HhzHOwb32twyQntl75HMLNf5E7hkH9aNTaSpn20ZThsyQC2Rt7fA_Wthz0osSgItW_WUiwA3MUa5-7GXquQCVL1uHLePUOUN9uVoiArBCm-l21DXJ51yVQ" />
    <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/chart?repos=hoainho/img2threejs&type=timeline&legend=top-left&sealed_token=HhzHOwb32twyQntl75HMLNf5E7hkH9aNTaSpn20ZThsyQC2Rt7fA_Wthz0osSgItW_WUiwA3MUa5-7GXquQCVL1uHLePUOUN9uVoiArBCm-l21DXJ51yVQ" />
    <img alt="Star History Chart" src="https://api.star-history.com/chart?repos=hoainho/img2threejs&type=timeline&legend=top-left&sealed_token=HhzHOwb32twyQntl75HMLNf5E7hkH9aNTaSpn20ZThsyQC2Rt7fA_Wthz0osSgItW_WUiwA3MUa5-7GXquQCVL1uHLePUOUN9uVoiArBCm-l21DXJ51yVQ" width="600" />
  </picture>
</a>

---

## 支持项目

img2threejs 免费且开源。如果它帮你省了时间、进了你的项目，欢迎支持持续开发：

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/O8A625YLSR)

VietQR / MoMo / PayPal 也行 —— 见[捐赠页](https://img2threejs.io/donate.html)。

---

## 赞助商

用代码重建首先是推理负载，其次才是图形活：每次门控重跑、每次渲染 vs 参考、每次材质拟合都在烧 token。是这三家在为这个循环买单。

<table>
  <tr>
    <td align="center" width="200">
      <a href="https://www.atlascloud.ai/console/coding-plan" target="_blank" rel="noopener noreferrer">
        <picture>
          <source media="(prefers-color-scheme: dark)" srcset="assets/sponsors/atlas-cloud-logomark-white.svg" />
          <source media="(prefers-color-scheme: light)" srcset="assets/sponsors/atlas-cloud-logomark-black.svg" />
          <img alt="Atlas Cloud" src="assets/sponsors/atlas-cloud-logomark-black.svg" width="72" height="67" />
        </picture>
      </a>
      <br /><sub><b>Atlas Cloud</b></sub>
      <br /><sub>Full-modal AI inference</sub>
    </td>
    <td align="center" width="200">
      <a href="https://www.tripo3d.ai/" target="_blank" rel="noopener noreferrer">
        <picture>
          <source media="(prefers-color-scheme: dark)" srcset="assets/sponsors/tripo-logomark-white.svg" />
          <source media="(prefers-color-scheme: light)" srcset="assets/sponsors/tripo-logomark-black.svg" width="68" height="68" />
        </picture>
      </a>
      <br /><sub><b>Tripo</b></sub>
      <br /><sub>Image &amp; text to 3D</sub>
    </td>
    <td align="center" width="200">
      <a href="https://hyper3d.ai/" target="_blank" rel="noopener noreferrer">
        <picture>
          <source media="(prefers-color-scheme: dark)" srcset="assets/sponsors/hyper3d-logomark-white.png" />
          <source media="(prefers-color-scheme: light)" srcset="assets/sponsors/hyper3d-logomark-black.png" />
          <img alt="Hyper3D" src="assets/sponsors/hyper3d-logomark-black.png" width="68" height="68" />
        </picture>
      </a>
      <br /><sub><b>Hyper3D</b></sub>
      <br /><sub>Rodin generative 3D</sub>
    </td>
  </tr>
</table>

### Atlas Cloud

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/sponsors/atlas-cloud-logomark-white.svg" />
  <source media="(prefers-color-scheme: light)" srcset="assets/sponsors/atlas-cloud-logomark-black.svg" />
  <img alt="" src="assets/sponsors/atlas-cloud-logomark-black.svg" width="38" height="36" align="right" />
</picture>

**[Atlas Cloud](https://www.atlascloud.ai/console/coding-plan)** 是全模态 AI 推理平台：视频生成、图像生成、LLM 访问一个 AI API 搞定，统一接入 300+ 精选模型，按模态全覆盖，不用每个厂商单独对接。

这个统一入口让本项目的循环负担得起 —— 管线按设计就是 token 大户，因为 spec 先过门控再写代码意味着分析要跑不止一遍。Atlas Cloud 的 coding plan 是拿到这个 API 的省钱路线。

**→ [打开 Atlas Cloud coding plan](https://www.atlascloud.ai/console/coding-plan)**

### Tripo

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/sponsors/tripo-logomark-white.svg" />
  <source media="(prefers-color-scheme: light)" srcset="assets/sponsors/tripo-logomark-black.svg" />
  <img alt="" src="assets/sponsors/tripo-logomark-black.svg" width="38" height="38" align="right" />
</picture>

**[Tripo](https://www.tripo3d.ai/)** 把提示词或参考图变成生产级 3D 资产：渲染/打印用的 2M 面高精度网格、实时引擎用的 500 到 50K 三角面艺术家级四边面 **Smart Mesh**、AI 自动骨骼、8K PBR 纹理、部件级分割。导出 GLB、FBX、OBJ、USD、STL、3MF，Blender、Unity、Unreal、Godot、Cocos、ComfyUI 官方插件全有。

它和 img2threejs 是互相校准的关系。程序化重建的生死看剪影、比例和关节位置，同一对象的四边面网格加自动骨骼能给这些门控第二个读数 —— 单张参考照片给不了。

**→ [打开 Tripo Studio](https://www.tripo3d.ai/)**

### Hyper3D

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/sponsors/hyper3d-logomark-white.png" />
  <source media="(prefers-color-scheme: light)" srcset="assets/sponsors/hyper3d-logomark-black.png" />
  <img alt="" src="assets/sponsors/hyper3d-logomark-black.png" width="38" height="38" align="right" />
</picture>

**[Hyper3D](https://hyper3d.ai/)** 的 **Rodin** 几秒钟就从提示词或图片生成 3D 资产，参考保真高、跨视角细节一致。生成可控不是掷骰子：包围盒/体素/点云 ControlNet 引导、局部编辑只改一个区域不动其余、智能低多边形优化、ChatAvatar 生产级绑定人脸。导出 STL、FBX、OBJ、GLB、glTF、USDZ。

它回答了单张照片永远回答不了的问题 —— 背面长什么样。生成对象、转一圈，藏起来的面就成了材质与表面门控真正能跑的参考，而不是管线只能悄悄假设的东西。

**→ [打开 Hyper3D Rodin](https://hyper3d.ai/)**

---

赞助解决的是算力账单，不是话语权：赞助商的产品在这里用它自己的话术描述，本仓库没有任何门控、默认项或基准偏向某一家。想把你的 logo 放进这一行？开 issue 或写邮件到 <hoainho.work@gmail.com>。

---

## 参与贡献

欢迎贡献 —— 程序化材质配方、新门控、宿主覆盖、演示尤其欢迎。先看 [CONTRIBUTING.md](CONTRIBUTING.md) 和[路线图](ROADMAP.md)了解项目方向。

## 许可证

Apache License 2.0，见 [LICENSE](LICENSE)。
