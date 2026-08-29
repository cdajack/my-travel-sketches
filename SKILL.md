---
name: my-travel-sketches
description: "Transform each supplied travel photo into its own hand-carved, distressed, spot-color rubber-stamp illustration on archival paper. Default to a small lower-left layout with a left-aligned caption; when explicitly requested, use a large centered layout with one stamp at about 50%–60% of the canvas width and centered text. Default to a 3:4 portrait canvas and honor a user-specified aspect ratio. Use for 橡皮章旅行记录、旅行观察小画、建筑地标章印、山岸船车人物的手工套色版画; do not include the source photo, repeated stamp units, photo-and-print diptychs, passport stamps, circular seals, souvenir logos, pure vector icons, or multi-photo collages."
---

# My Travel Sketches

中文名称：我的旅途小画

把旅行照片作为观察依据，将同一场景压缩成一幅克制、可辨认的手工多色橡皮章小画。原照片只用于提取事实、轮廓和色彩，不得出现在最终成品中。

## 默认交付

- 一张输入照片对应一张独立成品；多张照片逐张生成，禁止拼贴。
- 成品只呈现橡皮章版画、旧纸背景和小型归档文字，不显示、嵌入或并排放置原照片。
- 用户未指定比例时采用 `3:4`（宽:高）竖版；用户指定比例时以用户要求为准。
- 默认使用小版：章印与文字组成一个左下锚定的小型内容组；章印在上，文字在下且与章印左边缘对齐，画面上方和右侧保留大片未印刷纸白。
- 用户明确要求“大版”或“居中格式”时，切换为大版：画面中只出现一幅章印，水平居中，宽度约占画布的 50%–60%；文字置于章印下方并整体居中。未明确要求时不得使用大版。
- 归档文字默认添加当前年份；用户指定年份时使用用户提供的年份。
- 每张作品在一次图像生成或编辑中完成，不用代码硬拼。
- 图片任务只有在成品保存到工作区并在聊天中显示可见图片后才算完成。

## 请求模式

### Generate

用户提供照片并要求生成时：读取 [references/style-system.md](references/style-system.md) 与 [references/quality-gate.md](references/quality-gate.md)，确认输出比例和版式（默认小版；用户明确要求大版或居中格式时使用大版），分析照片后使用内置图像生成工具逐张完成。

### Prompt-only

用户只要提示词时：返回 [references/prompt.zh-CN.md](references/prompt.zh-CN.md) 的完整提示词。可以替换已确认的地点、标题、关键词、用户指定比例和年份，但不得删去“成品不出现原照片”与橡皮章媒介约束。

### Analyze

用户只要分析时：说明照片中应保留的主体、最适合雕刻的轮廓、建议的 2–4 种照片取样专色、构图、标题候选和潜在失败点；不要擅自生成图片。

## 工作流

1. 确定画幅。用户未指定时使用 `3:4` 竖版；指定后按用户比例设计构图。
2. 识别照片事实：主体、数量、姿态、建筑或地形结构、观察角度、空间方向、主色和可删除噪声。
3. 判断最值得刻下的 1–3 个视觉锚点。复杂场景不逐物复制，只保留能够认出原场景的线面关系。
4. 从照片提取 2–4 种专色：一组深色结构墨、一种主体特征色、可选的一种环境色与极小强调色。
5. 若地点可靠，提炼 1–3 个英文单词标题；地点不可靠时使用场景主题。年份默认使用当前年份，用户指定时使用指定年份；禁止猜测照片拍摄年份、历史年份、坐标或品牌。
6. 将照片事实、目标比例与 [references/prompt.zh-CN.md](references/prompt.zh-CN.md) 合并，逐张调用图像生成工具。上传照片仅作为参考图，不作为画面组成部分。
7. 按 [references/quality-gate.md](references/quality-gate.md) 检查。只修正明确失败点，不在迭代中更换主体或媒介逻辑。
8. 将成品保存到工作区，并把每张图片作为可见图片显示在聊天中。

## 不可破坏的规则

- 最终画面不得出现原照片、照片裁片、照片背景、左右对照、上下对照或画中画。
- 成品必须是真正重新雕刻和套印的图形，不是在照片上叠颗粒或盖章滤镜。
- 主体身份、数量、姿态、结构、方向和关键空间关系必须可从输入照片追溯；不得镜像或凭空新增地标。
- 默认小版时，章印位于画布左下区域，只占画布高度约 28%–38%；周围保留大面积纸白，不得擅自放大为满版插画。仅在用户明确要求大版时，才允许将章印放大为画布的主要视觉区域。
- 小版归档文字紧接章印下方并左对齐章印左边缘；大版归档文字位于章印下方并整体居中。文字不得与章印脱离。
- 每张成品只允许出现一幅由输入照片转化的章印；禁止把同一章印复制、重复排列、阵列或制作成无缝纹样。
- 使用 2–4 种从照片提取的低至中饱和专色，并具有缺墨、断边、针孔、颗粒和轻微 1–2 mm 套印错位。
- 归档文字必须少、小、准确，并默认包含当前年份；用户指定年份时以用户要求为准。不能确认地点时，不得生成具体地名。
- 禁止圆形印章、红色姓名章、蜡封、护照章、邮票齿孔、纪念品 Logo、光滑 SVG、水彩晕染、塑料 3D、摄影拼贴和产品样机。

## 视觉参考

只有在需要校准版式密度与印刷质感时，查看裁剪后的 `assets/examples/`。案例是媒介参考，不是内容模板；不得复制其中的意大利地标、标题或色盘，年份应按当前年份或用户指定年份生成。
