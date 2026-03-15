# Solar System Simulator

基于 Three.js 的太阳系运动仿真。

**在线演示**：<https://hencehzw.github.io/Solar-System-Simulator/>

## 快速开始

因 CORS 限制，需通过本地 HTTP 服务器运行：

```bash
# 进入项目目录
python -m http.server 8000
```

浏览器访问 `http://localhost:8000/`

## 主要特性

- **双比例模式**：展示比例（便于观察）与真实比例（贴近天文数据）
- **轨道系统**：椭圆轨道、轨道倾角、升交点与近心点参数；土星 / 天王星环
- **星体渲染**：太阳自定义着色器、地球日夜混合（城市灯光）、Bump Map 表面纹理（固体行星）
- **交互**：行星聚焦、信息面板、轨道开关、动画倍速与暂停

## 技术栈

Three.js · lil-gui · Tween.js · EffectComposer (UnrealBloomPass)

## 致谢

实现思路参考 [threejs-SolarSystem](https://github.com/licwits/threejs-SolarSystem)、[Solar-System-3D](https://github.com/N3rson/Solar-System-3D)，纹理源自 [Solar System Scope](https://www.solarsystemscope.com/textures/)。
