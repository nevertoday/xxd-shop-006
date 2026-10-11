---
name: xxd-shop-006
description: "Create XXD Shop 006 fabric and material showcase visuals (服装面料材质展示) as finished PNGs from garment or fabric photos plus their written specs, treating the bundled original brief as the sole aesthetic authority: first identify and research every unfamiliar fibre, yarn, weave, knit, laminate, finish or branded technology from reliable sources, separate material properties from process effects and marketing claims, then let the model choose macro weave, folds, drape, cross-section, water beading or raw-material cues to show what the cloth truly is, with minimal labels only for verified facts. Supports multiple ratios or exact sizes, several compositions per size, prompt-generated, user-exact or user-plan labels, or none. Use when the user invokes xxd-shop-006 or asks for 面料图、材质展示、面料卖点图、微距织纹、面料剖面、科技面料说明图."
---

# XXD Shop 006｜面料材质展示

用本次的服装或面料图片，加上面料名称、成分、工艺和卖点文字，生成“让人感受到这块布真正是什么样”的材质展示图，交付 PNG。

每次生成前，完整读取 `references/original-prompt/zh-CN.md`。这份中文原始提示词是唯一的创作与审美权威；不总结、不翻译、不混用，也不用本文件、README、样张或其他编号替代它。

每次构建生图请求前，完整读取 `references/shop-runtime.md`，它是唯一的家族运行合同。本 Skill 不另写第二套美术指导或运行规则。

所有成品直接写进 `~/Desktop/xxd/xxd-shop-006/` 下新建的一个任务目录（或 `--out` 指定的根目录），不建子目录，不自动拼总览。

## 本编号覆盖条款

**必须有商品图。** 原稿要求“严格参考用户提供的产品图，保留真实颜色、花纹、织法、纹理尺度和材质气质”。没有面料或服装图时只请用户上传，不凭文字想象一块布。

**原稿要求先查证，这一步由 Agent 在生图前完成。** 这是本编号与其他编号最大的不同：

1. **列出待查术语。** 从用户文字和吊牌、标签中，列出所有不熟悉、含义不确定、可能是行业术语、品牌技术名、新型材料、纱线名称、后整理工艺或复合结构的词。常见且无歧义的（纯棉、涤纶、羊毛）不必查。
2. **检索可靠资料。** 优先品牌官方资料、材料厂商技术说明、纺织行业资料、标准机构或专业文献。用户提供的未公开资料与商品图不送入检索。
3. **按原稿的九类归类：** 纤维原料、纱线结构、织造方式、针织组织、复合结构、表面处理、后整理工艺、功能技术，或单纯的商业命名。
4. **区分三种结论：** 材料本身的性质；特定工艺可能带来的效果；品牌宣传中的卖点。前两种有来源时可以视觉化；第三种没有独立证据时，不画成科学事实，不做功能演示。
5. **写进任务目录的 `facts.md`：**

```text
| 术语 | 归类 | 真实外观／结构 | 结论类型 | 来源 |
|---|---|---|---|---|
| <用户原词> | <九类之一> | <厚度、组织、孔隙、光泽、触感…> | 材料性质／工艺效果／宣传卖点（未证实） | <链接或用户提供> |
```

6. **把结论交给图像模型：** 已核实的条目写进本次商品块的“可用事实”；另起一行写“核心价值来源：<纱线织纹／柔软垂坠厚度／网眼透气排湿／防泼水表面处理／多层复合保暖／原料>”，对应原稿的六条分支。可以写一到两项，按用户卖点的先后排序；超过两项都成立时，问用户本张主打哪一项，或用 `--count` 每张主打一项。这一行是查证结论，不是外层的构图指令；用哪种视觉语言表现，仍由原稿和图像模型决定。

当前宿主没有检索工具时，告诉用户；只用用户提供的资料和图上可见的信息，未核实的术语标为“未证实”，不进入画面。

**标注只写已核实的内容。** `--text prompt` 时，画面上的每一条标注都必须能在 `facts.md` 或用户资料里找到；`--text none` 是纯材质图；`--text plan` 适合用户已有一段卖点文案的情况。

**追加验收：** 颜色、花纹、织法和纹理尺度与原图一致；没有把普通面料画成另一种更高级的材料；液滴、剖面、层厚符合真实材料；标注没有覆盖关键纹理；没有把未证实的宣传卖点画成功能演示。

## 参考文件

- `references/shop-runtime.md`：家族运行合同（含事实纪律与 `facts.md`）
- `references/original-prompt/zh-CN.md`：运行时使用的原始提示词
- `references/original-prompt/README.md`：译文索引与权威说明
- `references/runtime-preferences.md`：交付偏好沿用
- `references/sample-workflow.md`：仅用于维护样张
- `scripts/configured_imagegen.py`、`scripts/shop_preferences.py`
