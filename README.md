# 刘子超 — 漫游者的地图 | Liu Zichao Personal Website

旅行作家刘子超的个人网站，以"漫游者的地图"为核心，四段旅程、四本书。

## 项目结构

```
liu-zichao-website/
├── index.html              # 主页面（完整单文件，含CSS/JS/SVG）
├── README.md               # 本文件
└── images/                 # 旅途照片（待添加）
    ├── europe/             # 中欧 —《午夜降临前抵达》
    │   ├── berlin-01.jpg
    │   ├── praha-01.jpg
    │   └── ...
    ├── central-asia/       # 中亚 —《失落的卫星》
    │   ├── samarkand-01.jpg
    │   ├── pamir-01.jpg
    │   └── ...
    ├── monsoon-asia/       # 季风亚洲 —《沿着季风的方向》
    │   ├── india-01.jpg
    │   ├── myanmar-01.jpg
    │   └── ...
    └── balkans/            # 巴尔干 —《血与蜜之地》
        ├── bosnia-01.jpg
        ├── serbia-01.jpg
        └── ...
```

## 如何替换真实照片

当前城市照片为程序化生成的占位图。替换为真实照片只需两步：

### 1. 放入图片文件
将照片放入对应的 `images/` 子文件夹，建议命名格式：`城市名-序号.jpg`

### 2. 修改 index.html 中的照片数据
找到 `cityPhotos` 对象（约第530行），为每个城市的 photos 数组添加 `src` 字段：

```javascript
berlin:{city:'Berlin 柏林',book:'《午夜降临前抵达》',color:'#4a7c9b',photos:[
  {src:'images/europe/berlin-01.jpg', cap:'柏林街头游行', desc:'离开柏林那天...', hue:210},
  {src:'images/europe/berlin-02.jpg', cap:'勃兰登堡门前', desc:'冷战的阴影...', hue:220},
]},
```

然后在 `openLB()` 函数中将占位图替换为真实图片：

```javascript
// 替换这一行：
const img = makePlaceholder(p.hue, 600, 400);
// 改为：
const img = p.src || makePlaceholder(p.hue, 600, 400);
```

## 功能特性

- **全屏地图首页** — SVG世界地图，四条旅途路线自动描线动画
- **路线切换** — 右侧按钮切换高亮不同旅程，信息卡片联动
- **城市照片弹窗** — 点击地图上21个城市节点，弹出对应书中场景照片
- **书卡联动** — 鼠标悬停作品区书卡时，地图对应路线自动高亮
- **滚动动画** — 全站内容滚动渐入
- **全站暗色调** — 统一墨色地图美学

## 技术栈

- 纯 HTML/CSS/JS，无框架依赖
- SVG 手绘世界地图
- Canvas API 生成占位图
- Google Fonts: Playfair Display, EB Garamond, Noto Serif SC
- 响应式设计，适配移动端

## 后续可扩展方向

- 替换真实旅途照片
- 接入 Mapbox/Leaflet 实现可缩放拖拽地图
- 添加"书摘"板块，每个城市关联精选段落
- 多语言支持（中/英）
- 添加作者社交媒体链接
- SEO 和 Open Graph meta tags
