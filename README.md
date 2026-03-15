# Solar System Simulator / 太阳系星球运动仿真

基于 Three.js 的单页太阳系运动仿真，支持展示比例与真实比例双模式、椭圆轨道与轨道面朝向、行星聚焦与信息面板等交互。

## 项目说明

- **运行方式**：单页 HTML，使用 import map 直接加载 Three.js / lil-gui / Tween.js，无需构建。
- **入口**：在本地或静态服务器下打开 `index.html` 即可（纹理路径为相对路径，建议用本地服务器如 `npx serve .` 或 VS Code Live Server 打开 `experiment` 目录）。

## 主要功能

- **双比例模式**：展示比例（便于观察）、真实比例（轨道与尺寸更贴近真实）。
- **真实比例下的轨道**：椭圆轨道（偏心率、升交点、近心点角）、轨道倾角与空间朝向；展示比例下保持原圆轨道。
- **轨道线开关**：控制面板中可开关「行星轨道」显示。
- **行星与矮行星**：太阳、八大行星、冥王星；纹理与法线贴图，土星/天王星环（倾角与尺寸参考真实数据）。
- **小行星带**：火星与木星之间的小行星带。
- **地球与月球**：月球绕地公转、云层。
- **交互**：双击行星聚焦、右侧星图总览与星体索引、信息面板（轨道距离、质量、直径、自转/公转、温度及简介）。
- **控制演示**：动画倍速、暂停、比例模式、轨道显示开关。

## 技术栈

- Three.js（场景、相机、渲染、几何与材质）
- lil-gui（控制面板）
- @tweenjs/tween.js（聚焦/返回全景动画）
- 太阳：自定义顶点/片元着色器 + 耀斑 Sprite；行星：MeshStandardMaterial + 贴图/法线贴图

## 参考与致谢

本实验在**实现思路与部分实现方式**上参考了以下项目，并在此基础上做了独立实现与扩展。

### 参考项目

| 项目 | 链接 | 参考内容说明 |
|------|------|----------------|
| **threejs-SolarSystem** | [https://github.com/licwits/threejs-SolarSystem](https://github.com/licwits/threejs-SolarSystem) | 太阳系整体架构与部分实现思路：太阳的**自定义着色器**（顶点/片元）与**耀斑（Sprite）**表现方式；**行星轨道**的椭圆方程与**轨道倾角**的应用方式；**小行星带**的分布与运动思路；**点击行星切换视角**的交互方式；**可调节星球运动速度**的控制思路。该参考项目使用 Vite + Vue3 架构，本仓库为单页 Three.js 实现，未使用其源码，仅在上述思路上进行借鉴与改写。 |

### 本仓库的独立实现与扩展

- 单文件单页实现（无 Vue/Vite），采用 Three.js + lil-gui + Tween.js。
- **展示比例 / 真实比例**双模式及切换时的轨道与尺寸更新逻辑。
- **真实比例**下的完整轨道要素：偏心率、升交点经度、近心点幅角、轨道倾角，以及**三维轨道方程**直接计算轨道线与行星位置（避免高偏心率/高倾角下的错位与抖动）。
- 土星环、天王星环的**倾角与内外半径**按天文数据设置；轨道线**显示/隐藏**开关。
- 星图总览、星体索引、信息面板内容与样式，以及聚焦/返回全景的 Tween 动画。

## 资源与素材

- 行星表面贴图、法线贴图、环贴图等位于 `textures/` 下各子目录，部分来源可参考 [licwits/threejs-SolarSystem](https://github.com/licwits/threejs-SolarSystem) 的 README 中提到的：Celestia Motherlode、Solar System Scope、Poly Haven 等（本仓库未直接复用其资源包，仅作素材类型参考）。

## 目录结构（简要）

```
experiment/
├── index.html          # 主页面与全部逻辑
├── README.md           # 本说明
├── css/
│   └── style.css       # 若有额外样式
└── textures/           # 行星、太阳、环等贴图
    ├── Earth/
    ├── Saturn/
    ├── Uranus/
    ├── th_sun/
    └── …
```

## 许可证

本实验为课程作业/实验项目。参考项目 [licwits/threejs-SolarSystem](https://github.com/licwits/threejs-SolarSystem) 采用 MIT 许可证。
