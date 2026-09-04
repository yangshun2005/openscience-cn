# 市场研究报告可视化生成指南

用于在市场研究报告中生成可视化的完整提示词与指南。

---

## 概述

市场研究报告应首先包含 **5-6 个核心可视化**，以建立分析框架。在撰写具体章节时，可根据需要生成其他可视化。本指南为 `scientific-schematics` 和 `generate-image` 技能提供了可直接使用的提示词。

### 核心可视化（优先生成 - 优先级 1-6）

每份市场报告都应先生成以下 5-6 个核心可视化：

1. **市场增长轨迹图** - 展示市场规模趋势
2. **TAM/SAM/SOM 图** - 市场机会分解
3. **波特五力模型** - 竞争动态框架
4. **竞争定位矩阵** - 战略定位
5. **风险热力图** - 风险评估可视化
6. **执行摘要信息图**（可选）- 报告概览

### 扩展可视化（按需生成 - 优先级 7+）

在撰写过程中，当特定章节需要视觉支持时，可生成其他可视化：
- 区域细分图表
- 细分市场分析
- 客户旅程地图
- 技术路线图
- 监管时间线
- 财务预测
- 实施时间线

### 工具选择

| 可视化类型 | 工具 | 选择理由 |
|-------------|------|-----------|
| 图表（柱状图、折线图、饼图） | scientific-schematics | 精确的数据呈现 |
| 示意图（流程图、结构图） | scientific-schematics | 清晰的技术布局 |
| 矩阵图（2x2、定位图） | scientific-schematics | 战略框架 |
| 时间线 | scientific-schematics | 顺序信息展示 |
| 信息图 | generate-image | 创意视觉综合 |
| 概念插图 | generate-image | 抽象概念表达 |

---

## 可视化命名规范

### 核心可视化（优先生成）
```
figures/
├── 01_market_growth_trajectory.png      # 优先级 1
├── 02_tam_sam_som.png                   # 优先级 2
├── 03_porters_five_forces.png           # 优先级 3
├── 04_competitive_positioning.png       # 优先级 4
├── 05_risk_heatmap.png                  # 优先级 5
└── 06_exec_summary_infographic.png      # 优先级 6（可选）
```

### 扩展可视化（按需生成）
```
figures/
├── 07_industry_ecosystem.png
├── 08_regional_breakdown.png
├── 09_segment_growth.png
├── 10_driver_impact_matrix.png
├── 11_pestle_analysis.png
├── 12_trends_timeline.png
├── 13_market_share.png
├── 14_strategic_groups.png
├── 15_customer_segments.png
├── 16_segment_attractiveness.png
├── 17_customer_journey.png
├── 18_technology_roadmap.png
├── 19_innovation_curve.png
├── 20_regulatory_timeline.png
├── 21_risk_mitigation.png
├── 22_opportunity_matrix.png
├── 23_recommendation_priority.png
├── 24_implementation_timeline.png
├── 25_milestone_tracker.png
├── 26_financial_projections.png
└── 27_scenario_analysis.png
```

---

## 核心可视化（优先级 1-6）- 请优先生成

### 优先级 1：市场增长轨迹图

**工具：** scientific-schematics

**目的：** 展示历史及预测市场规模的基础可视化

**命令：**
```bash
python skills/scientific-schematics/scripts/generate_schematic.py \
  "Bar chart market growth 2020 to 2034. Historical bars 2020-2024 in dark blue, projected bars 2025-2034 in light blue. Y-axis billions USD, X-axis years. CAGR annotation. Data labels on each bar. Vertical dashed line between 2024 and 2025. Title: Market Growth Trajectory. Professional white background" \
  -o figures/01_market_growth_trajectory.png --doc-type report
```

---

### 优先级 2：TAM/SAM/SOM 图

**工具：** scientific-schematics

**目的：** 市场机会规模可视化

**命令：**
```bash
python skills/scientific-schematics/scripts/generate_schematic.py \
  "TAM SAM SOM concentric circles. Outer circle TAM Total Addressable Market. Middle circle SAM Serviceable Addressable Market. Inner circle SOM Serviceable Obtainable Market. Each labeled with acronym, full name, placeholder for dollar value. Arrows pointing to each with descriptions. Blue gradient darkest outer to lightest inner. White background professional appearance" \
  -o figures/02_tam_sam_som.png --doc-type report
```

---

### 优先级 3：波特五力模型图

**工具：** scientific-schematics

**目的：** 竞争动态框架

**命令：**
```bash
python skills/scientific-schematics/scripts/generate_schematic.py \
  "Porter's Five Forces diagram. Center box Competitive Rivalry with rating. Four surrounding boxes with arrows to center: Top Threat of New Entrants, Left Bargaining Power Suppliers, Right Bargaining Power Buyers, Bottom Threat of Substitutes. Color code HIGH red, MEDIUM yellow, LOW green. Include 2-3 key factors per box. Professional appearance" \
  -o figures/03_porters_five_forces.png --doc-type report
```

---

### 优先级 4：竞争定位矩阵

**工具：** scientific-schematics

**目的：** 关键市场参与者的战略定位

**命令：**
```bash
python skills/scientific-schematics/scripts/generate_schematic.py \
  "2x2 competitive positioning matrix. X-axis Market Focus Niche to Broad. Y-axis Solution Approach Product to Platform. Quadrants: Upper-right Platform Leaders, Upper-left Niche Platforms, Lower-right Product Leaders, Lower-left Specialists. Plot 8-10 company circles with names. Circle size = market share. Legend for sizes. Professional appearance" \
  -o figures/04_competitive_positioning.png --doc-type report
```

---

### 优先级 5：风险热力图

**工具：** scientific-schematics

**目的：** 可视化风险评估矩阵

**命令：**
```bash
python skills/scientific-schematics/scripts/generate_schematic.py \
  "Risk heatmap matrix. X-axis Impact Low Medium High Critical. Y-axis Probability Unlikely Possible Likely Very Likely. Cell colors: Green low risk, Yellow medium, Orange high, Red critical. Plot 10-12 numbered risks R1 R2 etc as labeled points. Legend with risk names. Professional clear" \
  -o figures/05_risk_heatmap.png --doc-type report
```

---

### 优先级 6：执行摘要信息图（可选）

**工具：** generate-image

**目的：** 用于封面或执行摘要的高层次视觉综合

**命令：**
```bash
python skills/generate-image/scripts/generate_image.py \
  "Executive summary infographic for market research, one page layout, central large metric showing market size, four quadrants showing growth rate key players top segments regional leaders, modern flat design, professional blue and green color scheme, clean white background, corporate business aesthetic" \
  --output figures/06_exec_summary_infographic.png
```

---

## 扩展可视化 - 在撰写过程中按需生成

以下可视化可在撰写需要它们的特定章节时生成。

---

## 前置可视化

### 扩展：封面图 / 主视觉

**工具：** generate-image

**提示词：**
```
Professional executive summary infographic for [MARKET NAME] market research report. 
Modern data visualization style showing key metrics: market size, growth rate, key players.
Blue and green color scheme matching corporate design.
Clean minimalist design with icons.
High resolution, publication quality.
No text overlays, image only.
```

**命令：**
```bash
python skills/generate-image/scripts/generate_image.py \
  "Professional executive summary infographic for [MARKET] market research report, modern data visualization style, key metrics display, blue and green corporate color scheme, clean minimalist design with icons, high resolution publication quality" \
  --output figures/01_cover_image.png
```

### 2. 执行摘要信息图

**工具：** generate-image

**提示词：**
```
One-page executive summary infographic showing:
- Large central metric: $XX billion market size
- Four quadrants with: Growth Rate, Key Players, Top Segments, Regional Leaders
- Modern flat design with data visualization elements
- Professional blue (#003366) and green (#008060) color scheme
- Clean white background
- Business/corporate aesthetic
```

**命令：**
```bash
python skills/generate-image/scripts/generate_image.py \
  "Executive summary infographic for market research, one page layout, central large metric showing market size, four quadrants showing growth rate key players top segments regional leaders, modern flat design, professional blue and green color scheme, clean white background, corporate business aesthetic" \
  --output figures/02_exec_summary_infographic.png
```

---

## 第 1 章：市场概览可视化

### 3. 行业生态系统图

**工具：** scientific-schematics

**提示词：**
```
Industry ecosystem value chain diagram showing horizontal flow from left to right:
[Suppliers/Inputs] → [Manufacturers/Processors] → [Distributors/Channels] → [End Users/Customers]

At each stage, show 3-4 example player types in smaller boxes below.
Use arrows to show product/service flow (solid) and money flow (dashed).
Include regulatory bodies as oversight layer above the chain.
Professional blue color scheme.
Clean white background.
All text clearly readable.
```

**命令：**
```bash
python skills/scientific-schematics/scripts/generate_schematic.py \
  "Industry ecosystem value chain diagram. Horizontal flow left to right: Suppliers box → Manufacturers box → Distributors box → End Users box. Below each main box show 3-4 smaller boxes with example player types. Solid arrows for product flow, dashed arrows for money flow. Regulatory oversight layer above. Professional blue color scheme, white background, clear labels" \
  -o figures/03_industry_ecosystem.png --doc-type report
```

### 4. 市场结构图

**工具：** scientific-schematics

**提示词：**
```
Market structure diagram showing concentric rectangles:
- Center: Core Market (labeled with market name)
- Second layer: Adjacent Markets (labeled with 4-5 adjacent market names)
- Third layer: Enabling Technologies (labeled with key technologies)
- Outer layer: Regulatory Framework

Use different shades of blue for each layer.
Include small icons or labels for key elements.
Professional appearance.
```

**命令：**
```bash
python skills/scientific-schematics/scripts/generate_schematic.py \
  "Market structure diagram with concentric rectangles. Center: Core Market [MARKET NAME]. Second layer: Adjacent Markets with 4-5 labels. Third layer: Enabling Technologies with key tech labels. Outer layer: Regulatory Framework. Different blue shades for each layer, professional appearance, clear labels" \
  -o figures/03b_market_structure.png --doc-type report
```

---

## 第 2 章：市场规模与增长可视化

### 5. 市场增长轨迹图

**工具：** scientific-schematics

**提示词：**
```
Bar chart showing market growth from 2020 to 2034.
Historical years (2020-2024): Dark blue bars
Projected years (2025-2034): Light blue bars
Y-axis: Market size in billions USD (0 to $XXX)
X-axis: Years
Include CAGR annotation showing "XX.X% CAGR (2024-2034)"
Data labels on top of each bar
Vertical dashed line separating historical from projected
Title: "[MARKET NAME] Market Growth Trajectory"
Professional appearance, white background
```

**命令：**
```bash
python skills/scientific-schematics/scripts/generate_schematic.py \
  "Bar chart market growth 2020 to 2034. Historical bars 2020-2024 in dark blue, projected bars 2025-2034 in light blue. Y-axis billions USD, X-axis years. CAGR annotation XX.X% (2024-2034). Data labels on each bar. Vertical dashed line between 2024 and 2025. Title: Market Growth Trajectory. Professional white background" \
  -o figures/04_market_growth_trajectory.png --doc-type report
```

### 6. TAM/SAM/SOM 图

**工具：** scientific-schematics

**提示词：**
```
TAM SAM SOM concentric circles diagram:
- Outer circle: TAM (Total Addressable Market) - $XXX billion
- Middle circle: SAM (Serviceable Addressable Market) - $XX billion  
- Inner circle: SOM (Serviceable Obtainable Market) - $X billion

Each circle labeled with:
- Acronym in bold
- Full name
- Dollar value

Arrows pointing to each circle with descriptions
Use blue color gradient (darkest for TAM, lightest for SOM)
Professional appearance
White background
```

**命令：**
```bash
python skills/scientific-schematics/scripts/generate_schematic.py \
  "TAM SAM SOM concentric circles. Outer circle TAM Total Addressable Market [VALUE]B. Middle circle SAM Serviceable Addressable Market [VALUE]B. Inner circle SOM Serviceable Obtainable Market [VALUE]B. Each labeled with acronym, full name, dollar value. Arrows pointing to each with descriptions. Blue gradient darkest outer to lightest inner. White background professional" \
  -o figures/05_tam_sam_som.png --doc-type report
```

### 7. 区域市场细分

**工具：** scientific-schematics

**提示词：**
```
Pie chart OR treemap showing regional market breakdown:
- North America: XX% ($X.XB) - Dark blue
- Europe: XX% ($X.XB) - Medium blue
- Asia-Pacific: XX% ($X.XB) - Teal
- Latin America: X% ($X.XB) - Light blue
- Middle East & Africa: X% ($X.XB) - Gray blue

Include both percentage and dollar value for each region
Legend on right side
Title: "Market Size by Region (2024)"
Professional appearance
```

**命令：**
```bash
python skills/scientific-schematics/scripts/generate_schematic.py \
  "Pie chart regional market breakdown. North America XX% dark blue, Europe XX% medium blue, Asia-Pacific XX% teal, Latin America XX% light blue, Middle East Africa XX% gray blue. Show percentage and dollar value for each slice. Legend on right. Title: Market Size by Region 2024. Professional appearance" \
  -o figures/06_regional_breakdown.png --doc-type report
```

### 8. 细分市场增长比较

**工具：** scientific-schematics

**提示词：**
```
Horizontal bar chart comparing segment growth rates:
- Y-axis: Segment names (5-7 segments)
- X-axis: CAGR percentage (0% to 30%)
- Bars colored by growth rate: Green (highest) to blue (lowest)
- Data labels showing exact percentage on each bar
- Sort segments from highest to lowest growth
- Title: "Segment Growth Rate Comparison (CAGR 2024-2034)"
- Include average line or marker
```

**命令：**
```bash
python skills/scientific-schematics/scripts/generate_schematic.py \
  "Horizontal bar chart segment growth comparison. Y-axis 5-7 segment names, X-axis CAGR percentage 0-30%. Bars colored green highest to blue lowest. Data labels with exact percentages. Sorted highest to lowest. Title: Segment Growth Rate Comparison CAGR 2024-2034. Include market average line" \
  -o figures/07_segment_growth.png --doc-type report
```

---

## 第 3 章：行业驱动因素与趋势可视化

### 9. 驱动因素影响矩阵

**工具：** scientific-schematics

**提示词：**
```
2x2 matrix for market driver assessment:
- X-axis: Impact on Market (Low → High)
- Y-axis: Probability of Occurrence (Low → High)
- Upper-right quadrant: "CRITICAL DRIVERS" (red/orange background)
- Upper-left quadrant: "MONITOR" (yellow background)
- Lower-right quadrant: "WATCH CAREFULLY" (yellow background)
- Lower-left quadrant: "LOWER PRIORITY" (green background)

Plot 8-10 drivers as labeled circles:
- Size of circle represents current market impact
- Position based on ratings

Include legend for circle sizes
Professional appearance with clear labels
```

**命令：**
```bash
python skills/scientific-schematics/scripts/generate_schematic.py \
  "2x2 matrix driver impact assessment. X-axis Impact Low to High, Y-axis Probability Low to High. Quadrants: Upper-right CRITICAL DRIVERS red, Upper-left MONITOR yellow, Lower-right WATCH CAREFULLY yellow, Lower-left LOWER PRIORITY green. Plot 8-10 labeled driver circles at appropriate positions. Circle size indicates current impact. Professional clear labels" \
  -o figures/08_driver_impact_matrix.png --doc-type report
```

### 10. PESTLE 分析图

**工具：** scientific-schematics

**提示词：**
```
PESTLE analysis hexagonal diagram:
- Center hexagon: "[MARKET NAME]" 
- Six surrounding hexagons connected to center:
  - Political (red/orange)
  - Economic (blue)
  - Social (green)
  - Technological (orange)
  - Legal (purple)
  - Environmental (teal)

Each outer hexagon contains 2-3 key bullet points
Connecting lines between center and outer hexagons
Professional appearance
Clear, readable text in each hexagon
```

**命令：**
```bash
python skills/scientific-schematics/scripts/generate_schematic.py \
  "PESTLE hexagonal diagram. Center hexagon labeled MARKET. Six surrounding hexagons: Political red, Economic blue, Social green, Technological orange, Legal purple, Environmental teal. Each outer hexagon has 2-3 bullet points of key factors. Lines connecting center to each. Professional appearance clear readable text" \
  -o figures/09_pestle_analysis.png --doc-type report
```

### 11. 行业趋势时间线

**工具：** scientific-schematics