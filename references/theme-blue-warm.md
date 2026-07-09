# 公众号排版组件库 —— 蓝橙简约

> **设计风格**：简约克制，蓝橙棕三色系统。蓝色（#2563EB）做主色用于锚点，橙色（#D97706）做点缀高亮，暖棕色（#4A3728）做正文。留白充沛，边框细淡，无重阴影。适合教程、深度分析、观点、知识整理类文章。

> **公众号平台限制须知**：
> - ❌ 不支持 `<style>`/`<script>`、CSS class/id、`position:fixed/absolute`、`float`、`@media`/`@keyframes`、`display:grid`
> - ✅ 支持内联 `style`、`display:flex`（有限）、`linear-gradient`、`border-radius`、`box-shadow`、`<section>/<p>/<span>/<strong>/<img>` 等基础标签

> **WeChat 兼容铁律**：
> - 装饰性空元素内部必须放 `<span leaf=""><br></span>` 占位
> - 不要把 `font-size`/`border-bottom` 打在 `<strong>` 上；不在同一个 `<p>` 里混多个不同 `font-size`
> - 结构化区域（如封面右侧图片槽位）没有内容时整块删掉

---

## 设计变量速查表

```
主色（蓝）：     #2563EB    锚点、封面标题、关键元素
强调色（橙）：   #D97706    高亮、标签、强调
正文色（棕）：   #4A3728    正文，温暖耐读

浅蓝底：        #EFF6FF    引用块、提示卡底色
浅橙底：        #FFFBEB    高亮、标签底色
暖灰底：        #FAF7F4    卡片、容器底色
极浅暖底：      #FCFAF8    页面基底

标题色：        #1E293B    深蓝灰（标题用）
正文色：        #4A3728    暖棕
次要文字：      #6B5E52    暖灰棕
注释/标签：     #9CA3AF    中性灰
辅助文字：      #B0A89C    浅暖灰

分割线：        #E2DDD8    暖灰
边框：          #E5DFD9    暖灰边框
极浅灰：        #F5F2ED    极淡暖灰

正文字号：      14px（不可改）
正文行高：      1.9
字间距：        0.5px
最大宽度：      677px
内容区边距：    0 20px

下划线 CSS：    border-bottom:2px solid #BFDBFE;font-weight:600;
```

字体栈：`-apple-system,BlinkMacSystemFont,'PingFang SC','Hiragino Sans GB','Microsoft YaHei',sans-serif`

---

## 组件 1 全局容器

```html
<section style="max-width:677px;margin:0 auto;background:#ffffff;font-family:-apple-system,BlinkMacSystemFont,'PingFang SC','Hiragino Sans GB','Microsoft YaHei',sans-serif;color:#4A3728;line-height:1.75;letter-spacing:0.5px;overflow-x:hidden;">

  <!-- 所有组件放在这里 -->

</section>
```

---

## 组件 2 封面 cover-breaking

> **文案策略**：封面标题和公众号外标题是两层标题，必须视角错开。封面标题从五个视角（数字反差/角色革命/案例串/方法论/情绪钩子）自选一个直出。

**无右侧图片版（推荐，更简约）**：

```html
<section style="margin:0 0 32px;background:#fff;border:1px solid rgba(37,99,235,0.12);border-radius:16px;overflow:hidden;box-shadow:0 2px 12px rgba(0,0,0,0.04);width:100%;">
  <section style="padding:32px 28px 20px;">
    <section style="display:flex;align-items:center;gap:8px;margin-bottom:20px;">
      <span style="width:6px;height:6px;background:#2563EB;border-radius:50%;"><span leaf=""><br></span></span>
      <span style="font-size:11px;font-weight:700;letter-spacing:3px;color:#2563EB;"><span leaf="">{{顶部标签}}</span></span>
      <section style="flex:1;height:1px;overflow:hidden;background:linear-gradient(to right,rgba(37,99,235,0.1),transparent);"><span leaf=""><br></span></section>
      <span style="font-size:10px;color:#D1D5DB;font-weight:600;"><span leaf="">{{日期}}</span></span>
    </section>
    <section>
      <p style="font-size:24px;font-weight:900;color:#1E293B;margin:0 0 12px;line-height:1.2;letter-spacing:-1px;">
        <span leaf="">{{主标题}}</span>
        <span style="color:#2563EB;"><span leaf="">{{蓝色高亮词}}</span></span>
      </p>
      <section style="width:36px;height:3px;background:#2563EB;border-radius:2px;margin-bottom:12px;">
        <span leaf=""><br></span>
      </section>
      <p style="font-size:13px;color:#9CA3AF;margin:0;line-height:1.7;">
        <span leaf="">{{副标题/关键词}}</span>
      </p>
    </section>
  </section>
  <section style="background:#2563EB;padding:10px 28px;display:flex;align-items:center;justify-content:space-between;">
    <p style="font-size:12px;color:rgba(255,255,255,0.9);margin:0;font-weight:600;letter-spacing:0.5px;">
      <span leaf="">{{底部左侧文字}}</span>
    </p>
    <section style="display:flex;gap:4px;">
      <span style="background:rgba(255,255,255,0.15);padding:1px 6px;border-radius:3px;font-size:8px;color:#fff;"><span leaf="">{{标签1}}</span></span>
      <span style="background:rgba(255,255,255,0.15);padding:1px 6px;border-radius:3px;font-size:8px;color:#fff;"><span leaf="">{{标签2}}</span></span>
    </section>
  </section>
</section>
```

**有右侧图片版**（有封面头像图时使用）：

```html
<section style="margin:0 0 32px;background:#fff;border:1px solid rgba(37,99,235,0.12);border-radius:16px;overflow:hidden;box-shadow:0 2px 12px rgba(0,0,0,0.04);width:100%;">
  <section style="padding:32px 28px 20px;">
    <section style="display:flex;align-items:center;gap:8px;margin-bottom:20px;">
      <span style="width:6px;height:6px;background:#2563EB;border-radius:50%;"><span leaf=""><br></span></span>
      <span style="font-size:11px;font-weight:700;letter-spacing:3px;color:#2563EB;"><span leaf="">{{顶部标签}}</span></span>
      <section style="flex:1;height:1px;overflow:hidden;background:linear-gradient(to right,rgba(37,99,235,0.1),transparent);"><span leaf=""><br></span></section>
      <span style="font-size:10px;color:#D1D5DB;font-weight:600;"><span leaf="">{{日期}}</span></span>
    </section>
    <section style="display:flex;align-items:center;gap:20px;">
      <section style="flex:1;min-width:0;">
        <p style="font-size:24px;font-weight:900;color:#1E293B;margin:0 0 12px;line-height:1.2;letter-spacing:-1px;">
          <span leaf="">{{主标题}}</span>
          <span style="color:#2563EB;"><span leaf="">{{蓝色高亮词}}</span></span>
        </p>
        <section style="width:36px;height:3px;background:#2563EB;border-radius:2px;margin-bottom:12px;">
          <span leaf=""><br></span>
        </section>
        <p style="font-size:13px;color:#9CA3AF;margin:0;line-height:1.7;">
          <span leaf="">{{副标题}}</span>
        </p>
      </section>
      <section style="flex-shrink:0;width:100px;height:100px;border-radius:12px;overflow:hidden;background:linear-gradient(135deg,#EFF6FF,#DBEAFE);display:flex;align-items:center;justify-content:center;border:1px solid rgba(37,99,235,0.08);">
        <!-- 封面右侧图片，保留原图代码 -->
      </section>
    </section>
  </section>
  <section style="background:#2563EB;padding:10px 28px;display:flex;align-items:center;justify-content:space-between;">
    <p style="font-size:12px;color:rgba(255,255,255,0.9);margin:0;font-weight:600;"><span leaf="">{{底部左侧文字}}</span></p>
    <section style="display:flex;gap:4px;">
      <span style="background:rgba(255,255,255,0.15);padding:1px 6px;border-radius:3px;font-size:8px;color:#fff;"><span leaf="">{{标签1}}</span></span>
    </section>
  </section>
</section>
```

---

## 组件 3 目录 toc-scroll（横向滚动目录）

2 个及以上章节时生成。第一个卡片蓝色高亮，最后一个固定为"写在最后"（PART ///）。

```html
<section style="margin:0 20px 32px;">
  <section style="display:flex;align-items:center;justify-content:space-between;margin-bottom:10px;">
    <p style="font-size:10px;color:#9CA3AF;margin:0;text-transform:uppercase;letter-spacing:2px;font-weight:600;">
      <span leaf="">📦 {{N}} Parts + Conclusion</span>
    </p>
    <p style="font-size:10px;color:#9CA3AF;margin:0;">
      <span leaf="">👉 滑动</span>
    </p>
  </section>
  <section style="overflow-x:scroll;-webkit-overflow-scrolling:touch;white-space:nowrap;padding-bottom:8px;">
    <!-- 第一个（当前高亮，蓝色背景） -->
    <section style="display:inline-block;white-space:normal;vertical-align:top;width:110px;background:#2563EB;border-radius:12px;padding:12px;margin-right:8px;">
      <p style="font-size:9px;font-weight:700;color:rgba(255,255,255,0.7);letter-spacing:1px;margin:0 0 5px;"><span leaf="">PART 01</span></p>
      <p style="font-size:13px;font-weight:800;color:#fff;margin:0 0 3px;"><span leaf="">{{章节名}}</span></p>
      <p style="font-size:10px;color:rgba(255,255,255,0.7);margin:0;"><span leaf="">{{副标题}}</span></p>
    </section>
    <!-- 后续章节（白色背景），按需重复 -->
    <section style="display:inline-block;white-space:normal;vertical-align:top;width:110px;background:#fff;border:1px solid #E5DFD9;border-radius:12px;padding:12px;margin-right:8px;box-shadow:0 1px 4px rgba(0,0,0,0.03);">
      <p style="font-size:9px;font-weight:700;color:#9CA3AF;letter-spacing:1px;margin:0 0 5px;"><span leaf="">PART 02</span></p>
      <p style="font-size:13px;font-weight:800;color:#1E293B;margin:0 0 3px;"><span leaf="">{{章节名}}</span></p>
      <p style="font-size:10px;color:#9CA3AF;margin:0;"><span leaf="">{{副标题}}</span></p>
    </section>
    <!-- 最后一个（写在最后） -->
    <section style="display:inline-block;white-space:normal;vertical-align:top;width:110px;background:#fff;border:1px solid #E5DFD9;border-radius:12px;padding:12px;box-shadow:0 1px 4px rgba(0,0,0,0.03);">
      <p style="font-size:9px;font-weight:700;color:#9CA3AF;letter-spacing:1px;margin:0 0 5px;"><span leaf="">PART ///</span></p>
      <p style="font-size:13px;font-weight:800;color:#1E293B;margin:0 0 3px;"><span leaf="">写在最后</span></p>
      <p style="font-size:10px;color:#9CA3AF;margin:0;"><span leaf="">{{副标题}}</span></p>
    </section>
  </section>
</section>
```

---

## 组件 4 章节标题 chapter-title

第一个章节用 `margin-top:16px`，后续章节用 `margin-top:48px`。最后一章编号用 `///`，PART 改为 `LAST`。

```html
<section style="margin-top:48px;margin-bottom:32px;padding:0 20px;">
  <section style="display:flex;align-items:center;gap:14px;margin-bottom:24px;">
    <section style="text-align:center;flex-shrink:0;">
      <p style="margin:0;font-size:26px;font-weight:900;color:#2563EB;line-height:1;letter-spacing:-2px;">
        <span leaf="">{{01}}</span>
      </p>
      <p style="margin:0;font-size:8px;font-weight:700;color:#D1D5DB;letter-spacing:2px;">
        <span leaf="">PART</span>
      </p>
    </section>
    <span style="width:1px;height:32px;background:#E2DDD8;flex-shrink:0;"><span leaf=""><br></span></span>
    <section>
      <p style="margin:0 0 1px;font-size:16px;font-weight:900;color:#1E293B;letter-spacing:0.3px;">
        <span leaf="">{{中文标题}}</span>
      </p>
      <p style="margin:0;font-size:11px;font-weight:600;color:#9CA3AF;letter-spacing:1.5px;">
        <span leaf="">{{ENGLISH · 副标题}}</span>
      </p>
    </section>
  </section>
</section>
```

---

## 组件 5 正文段落 paragraph

```html
<p style="margin-bottom:16px;font-size:14px;line-height:1.9;text-align:justify;">
  <span leaf="">{{正文内容}}</span>
</p>
```

段间距较大时用 `margin-bottom:24px`。

---

## 组件 6 行内样式（9 种 + 使用原则）

### 6a. 蓝色加粗（核心概念、关键结论、品牌名）

```html
<strong style="color:#2563EB;"><span leaf="">文字</span></strong>
```

### 6b. 蓝色背景标签

```html
<strong style="color:#2563EB;background:rgba(37,99,235,0.08);padding:0 4px;border-radius:2px;"><span leaf="">文字</span></strong>
```

### 6c. 橙色渐变高亮（每段 ≤1-2 处）

```html
<span style="background:linear-gradient(120deg,#FDE68A 0%,rgba(255,255,255,0) 100%);padding:0 4px;border-radius:2px;font-weight:600;color:#1E293B;"><span leaf="">文字</span></span>
```

### 6d. 橙色底部高亮

```html
<span style="color:#1E293B;font-weight:bold;border-bottom:3px solid #FDE68A;"><span leaf="">文字</span></span>
```

### 6e. 蓝色下划线（**正文关键词的默认标记**）

```html
<span style="border-bottom:2px solid #BFDBFE;font-weight:600;"><span leaf="">文字</span></span>
```

### 6f. 红色下划线（对比、否定）

```html
<span style="border-bottom:2px solid #FECACA;"><span leaf="">文字</span></span>
```

### 6g. 代码标签（行内代码）

```html
<span style="background:#F3F4F6;color:#1F2937;padding:2px 6px;border-radius:4px;font-size:13px;font-weight:600;"><span leaf="">code</span></span>
```

### 6h. 获取方式标签（橙色背景）

```html
<span style="background:#FDE68A;color:#1F2937;padding:2px 6px;border-radius:4px;font-size:13px;font-weight:700;"><span leaf="">「关键词」</span></span>
```

### 6i. 删除线灰色（旧的/被淘汰的概念）

```html
<span style="background:#F3F4F6;color:#6B7280;padding:2px 6px;border-radius:4px;font-size:13px;text-decoration:line-through;font-weight:600;"><span leaf="">旧词</span></span>
```

**使用原则**：
1. 蓝色加粗用于核心概念、品牌名（全文 ≤5 处）
2. 橙色高亮每段 ≤1-2 处
3. 蓝色下划线用于正文关键词逐段标记（默认）
4. 红色下划线只用于对比/否定
5. 一段文字中不要同时使用超过 2 种高亮效果

---

## 组件 7 内容标签组（STEP / CASE / SKILL）

### 7a. step-label（STEP 步骤标签）

```html
<section style="margin-bottom:24px;">
  <section style="display:flex;align-items:center;gap:8px;margin-bottom:10px;">
    <span style="display:inline-block;background:#2563EB;color:#fff;font-size:10px;font-weight:700;padding:2px 8px;border-radius:4px;"><span leaf="">STEP 01</span></span>
    <h4 style="font-size:15px;font-weight:800;color:#1E293B;margin:0;"><span leaf="">{{步骤标题}}</span></h4>
  </section>
  <p style="font-size:14px;margin:0 0 16px;color:#4A3728;line-height:1.9;">{{步骤内容}}</p>
</section>
```

### 7b. case-label（CASE 案例标签）

```html
<section style="margin-bottom:28px;">
  <section style="display:flex;align-items:center;gap:8px;margin-bottom:10px;">
    <span style="display:inline-block;background:#E5DFD9;color:#6B5E52;font-size:10px;font-weight:700;padding:2px 8px;border-radius:4px;"><span leaf="">CASE 01</span></span>
    <h4 style="font-size:15px;font-weight:800;color:#1E293B;margin:0;"><span leaf="">{{案例标题}}</span></h4>
  </section>
</section>
```

### 7c. skill-label / tool-label

```html
<section style="margin-bottom:28px;">
  <section style="display:flex;align-items:center;gap:8px;margin-bottom:10px;">
    <span style="display:inline-block;background:#2563EB;color:#fff;font-size:10px;font-weight:700;padding:2px 8px;border-radius:4px;"><span leaf="">SKILL 1</span></span>
    <h4 style="font-size:15px;font-weight:800;color:#1E293B;margin:0;"><span leaf="">{{名称}}</span></h4>
  </section>
</section>
```

---

## 组件 8 代码/命令/Prompt

### 8a. prompt-block

```html
<p style="font-size:13px;color:#4A3728;margin:0 0 16px;line-height:1.8;">
  <span style="display:inline-block;background:#2563EB;color:#fff;font-size:11px;font-weight:700;padding:1px 7px;border-radius:3px;margin-right:6px;vertical-align:middle;letter-spacing:0.5px;"><span leaf="">PROMPT</span></span>
  <span style="font-size:12px;color:#9CA3AF;font-weight:700;"><span leaf="">{{提示词}}</span></span>
</p>
```

### 8b. cmd-block

```html
<p style="font-size:13px;color:#4A3728;margin:0 0 24px;line-height:1.8;">
  <span style="display:inline-block;background:#1E293B;color:#fff;font-size:11px;font-weight:700;padding:1px 7px;border-radius:3px;margin-right:6px;vertical-align:middle;letter-spacing:0.5px;"><span leaf="">CMD</span></span>
  <span style="background:#F3F4F6;color:#1F2937;padding:2px 6px;border-radius:4px;font-size:13px;font-weight:600;"><span leaf="">{{命令内容}}</span></span>
</p>
```

### 8c. 多行代码块 → 用通用增量库

多行代码块直接用 `common-components.md` 的 1a 深色代码块；浅色场景用 1b 并把左竖条换成 `#2563EB`。

---

## 组件 9 引用与亮点

### 9a. quote-box（蓝色竖条引用框）

```html
<section style="background:#F5F2ED;border-left:3px solid #2563EB;border-radius:4px;padding:12px 16px;margin-bottom:20px;">
  <p style="font-size:13px;color:#4A3728;margin:0;line-height:1.7;">
    {{引用内容}}
  </p>
</section>
```

### 9b. oneliner-card（橙色亮点卡片）

单行版：

```html
<section style="background:#FFF;border:1px solid #FDE68A;border-radius:10px;padding:14px 18px;margin-bottom:20px;text-align:center;">
  <p style="font-size:12px;color:#9CA3AF;margin:0 0 6px;line-height:1.5;"><span leaf="">{{引导语}}</span></p>
  <p style="margin:0;line-height:1.6;">
    <span style="font-size:15px;color:#D97706;font-weight:bold;border-bottom:3px solid #FDE68A;padding-bottom:2px;"><span leaf="">{{亮点内容}}</span></span>
  </p>
</section>
```

### 9c. subtitle-highlight（橙色底划线小节标题）

```html
<p style="font-size:15px;font-weight:900;color:#1E293B;margin-bottom:16px;">
  <span style="background:linear-gradient(180deg,transparent 65%,#FDE68A 65%);padding:0 4px;"><span leaf="">{{小节标题}}</span></span>
</p>
```

### 9d. center-divider（居中金句分隔）

```html
<p style="font-size:14px;margin-bottom:20px;text-align:center;color:#2563EB;font-weight:700;letter-spacing:1px;border-top:1px solid #F5F2ED;border-bottom:1px solid #F5F2ED;padding:12px 0;">
  <span leaf="">{{居中金句}}</span>
</p>
```

---

## 组件 10 提示与信息

### 10a. warn-tip（踩坑提示）

```html
<section style="padding:6px 0 4px;margin-bottom:16px;">
  <p style="margin-bottom:6px;font-size:12px;font-weight:700;color:#9CA3AF;letter-spacing:1px;">
    <span style="color:rgb(255,76,0);"><span leaf="">！踩坑提示 🕳</span></span>
  </p>
  <p style="font-size:13px;color:#4A3728;margin:0;line-height:1.7;">
    <span style="color:rgb(136,136,136);font-weight:bold;"><span leaf="">{{提示内容}}</span></span>
  </p>
</section>
```

### 10b. blue-tip（蓝色提示）

```html
<section style="padding:6px 0 4px;margin-bottom:16px;">
  <p style="margin-bottom:6px;font-size:12px;font-weight:700;color:#9CA3AF;letter-spacing:1px;">
    <span style="color:#2563EB;"><span leaf="">✦ {{提示标题}}</span></span>
  </p>
  <p style="font-size:13px;color:#4A3728;margin:0;line-height:1.7;">{{提示内容}}</p>
</section>
```

### 10c. orange-warning（橙色警告框）

```html
<section style="background:#FFFBEB;border:1px solid #FDE68A;border-radius:10px;padding:12px 16px;margin-bottom:20px;">
  <p style="font-size:13px;color:#92400E;margin:0;font-weight:700;">
    <span leaf="">{{警告内容}}</span>
  </p>
</section>
```

### 10d. blue-info（蓝色信息框）

```html
<section style="background:#EFF6FF;padding:12px 16px;border-radius:8px;border:1px solid #BFDBFE;margin-bottom:20px;">
  <p style="font-size:13px;color:#1E293B;margin:0;line-height:1.7;">{{信息内容}}</p>
</section>
```

---

## 组件 11 布局组件

### 11a. pill-list（蓝色胶囊列表）

```html
<section style="margin-bottom:14px;">
  <p style="margin:0 0 8px;font-size:14px;">
    <span style="display:inline-block;font-size:13px;font-weight:700;color:#2563EB;background:rgba(37,99,235,0.06);padding:3px 10px;border-radius:999px;">
      <span style="display:inline-block;width:6px;height:6px;background:#2563EB;border-radius:50%;margin-right:5px;vertical-align:middle;"><span leaf=""><br></span></span>
      <span leaf="">{{标题}}</span>
    </span>
  </p>
  <p style="font-size:13px;color:#4A3728;margin:0;line-height:1.7;"><span leaf="">{{描述}}</span></p>
</section>
```

### 11b. ordered-list（数字编号列表）

```html
<section style="margin-bottom:24px;">
  <section style="display:flex;align-items:flex-start;gap:10px;margin-bottom:10px;">
    <span style="display:inline-flex;align-items:center;justify-content:center;width:22px;height:22px;background:#2563EB;color:#fff;font-size:11px;font-weight:700;border-radius:6px;flex-shrink:0;margin-top:2px;"><span leaf="">1</span></span>
    <p style="font-size:14px;color:#4A3728;margin:0;line-height:1.9;flex:1;"><span leaf="">{{列表项内容}}</span></p>
  </section>
  <section style="display:flex;align-items:flex-start;gap:10px;">
    <span style="display:inline-flex;align-items:center;justify-content:center;width:22px;height:22px;background:#D97706;color:#fff;font-size:11px;font-weight:700;border-radius:6px;flex-shrink:0;margin-top:2px;"><span leaf="">2</span></span>
    <p style="font-size:14px;color:#4A3728;margin:0;line-height:1.9;flex:1;"><span leaf="">{{列表项内容}}</span></p>
  </section>
</section>
```

### 11c. table（表格）

```html
<section style="margin-bottom:24px;overflow-x:auto;">
  <table style="width:100%;border-collapse:collapse;font-size:13px;">
    <thead>
      <tr>
        <th style="background:#2563EB;color:#fff;font-weight:700;padding:8px 12px;text-align:left;"><span leaf="">{{列标题1}}</span></th>
        <th style="background:#2563EB;color:#fff;font-weight:700;padding:8px 12px;text-align:left;"><span leaf="">{{列标题2}}</span></th>
        <th style="background:#2563EB;color:#fff;font-weight:700;padding:8px 12px;text-align:left;"><span leaf="">{{列标题3}}</span></th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td style="padding:8px 12px;border-bottom:1px solid #E2DDD8;color:#4A3728;"><span leaf="">{{内容}}</span></td>
        <td style="padding:8px 12px;border-bottom:1px solid #E2DDD8;color:#4A3728;"><span leaf="">{{内容}}</span></td>
        <td style="padding:8px 12px;border-bottom:1px solid #E2DDD8;color:#4A3728;"><span leaf="">{{内容}}</span></td>
      </tr>
      <tr>
        <td style="padding:8px 12px;border-bottom:1px solid #E2DDD8;color:#4A3728;background:#FCFAF8;"><span leaf="">{{内容}}</span></td>
        <td style="padding:8px 12px;border-bottom:1px solid #E2DDD8;color:#4A3728;background:#FCFAF8;"><span leaf="">{{内容}}</span></td>
        <td style="padding:8px 12px;border-bottom:1px solid #E2DDD8;color:#4A3728;background:#FCFAF8;"><span leaf="">{{内容}}</span></td>
      </tr>
    </tbody>
  </table>
</section>
```

---

## 组件 12 媒体组件

### 12a. image（图片容器）

```html
<section style="background:#FFF;border-radius:10px;padding:4px;border:1px solid #E5DFD9;margin-bottom:6px;">
  <section style="margin:0;border-radius:8px;overflow:hidden;">
    <span leaf=""><img src="{{图片URL}}" style="max-width:100%;height:auto;display:block;margin:0 auto;"></span>
  </section>
</section>
<p style="font-size:12px;color:#9CA3AF;text-align:center;margin:0 0 24px;">
  <span leaf="">— {{图片说明}} —</span>
</p>
```

无说明文字时删掉下方 `<p>`。

### 12b. GIF 动图

```html
<section style="background:#FFF;border-radius:10px;padding:4px;border:1px solid #E5DFD9;margin-bottom:6px;">
  <section style="margin:0;border-radius:8px;overflow:hidden;">
    <span leaf=""><img src="{{动图URL}}.gif" style="max-width:100%;height:auto;display:block;margin:0 auto;"></span>
  </section>
</section>
<p style="text-align:center;margin:0 0 24px;">
  <span style="display:inline-block;background:#EFF6FF;color:#2563EB;font-size:11px;font-weight:700;padding:1px 8px;border-radius:4px;margin-right:6px;"><span leaf="">GIF 动图</span></span>
  <span style="font-size:12px;color:#9CA3AF;"><span leaf="">{{动图说明}}</span></span>
</p>
```

---

## 组件 13 结尾组件

### 13a. footer-cta（互动三连区，即签名/CTA 区）

```html
<section style="background:#FCFAF8;border:1px solid #E5DFD9;border-radius:12px;padding:24px 20px;text-align:center;margin:0 20px 24px;">
  <p style="font-size:13px;font-weight:bold;color:#1E293B;margin-bottom:16px;line-height:1.6;">
    <span leaf="">如果觉得有收获，欢迎点赞、在看、转发三连 🧡</span>
  </p>
  <section style="display:flex;justify-content:center;gap:24px;margin-bottom:12px;">
    <section style="text-align:center;">
      <section style="width:36px;height:36px;display:flex;align-items:center;justify-content:center;margin:0 auto 4px;background:#fff;border-radius:10px;border:1px solid #F5F2ED;">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#4A3728" stroke-width="1.8"><path d="M14 9V5a3 3 0 0 0-3-3l-4 9v11h11.28a2 2 0 0 0 2-1.7l1.38-9a2 2 0 0 0-2-2.3zM7 22H4a2 2 0 0 1-2-2v-7a2 2 0 0 1 2-2h3"></path></svg>
      </section>
      <span style="font-size:9px;font-weight:600;color:#4A3728;"><span leaf="">点赞</span></span>
    </section>
    <section style="text-align:center;">
      <section style="width:36px;height:36px;display:flex;align-items:center;justify-content:center;margin:0 auto 4px;background:#fff;border-radius:10px;border:1px solid #F5F2ED;">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#4A3728" stroke-width="1.8"><circle cx="12" cy="12" r="3"></circle><path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"></path></svg>
      </section>
      <span style="font-size:9px;font-weight:600;color:#4A3728;"><span leaf="">在看</span></span>
    </section>
    <section style="text-align:center;">
      <section style="width:36px;height:36px;display:flex;align-items:center;justify-content:center;margin:0 auto 4px;background:#EFF6FF;border-radius:10px;border:1px solid #BFDBFE;">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#2563EB" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M4 18v-4a8 8 0 0 1 8-8h8"></path><polyline points="16 2 20 6 16 10"></polyline></svg>
      </section>
      <span style="font-size:9px;font-weight:600;color:#2563EB;"><span leaf="">转发</span></span>
    </section>
  </section>
  <p style="font-size:9px;color:#9CA3AF;letter-spacing:1px;margin:0;"><span leaf="">THANKS FOR READING</span></p>
</section>
```

**签名文案适配**：SKILL.md 的作者签名以正文段落（组件 5）形式放在 footer-cta **之前**。默认用 `{{作者名}}` 占位，原文已有签名则沿用。

### 13b. brand-card（品牌尾图）

```html
<section style="text-align:center;" nodeleaf="">
  <!-- 保留原始品牌尾图代码不修改 -->
</section>
```

有素材时放在 footer-cta 之后，无素材整块省略。

---

## 完整文章模板骨架

```html
<section style="max-width:677px;margin:0 auto;background:#ffffff;font-family:-apple-system,BlinkMacSystemFont,'PingFang SC','Hiragino Sans GB','Microsoft YaHei',sans-serif;color:#4A3728;line-height:1.75;letter-spacing:0.5px;overflow-x:hidden;">

  <!-- 1. 封面（组件2，有图/无图二选一，推荐无图版） -->

  <!-- 2. 目录（组件3 toc-scroll，2+ 章节时生成，紧跟封面之下） -->

  <!-- 3. 开头引言（组件9b oneliner-card，文章有开头金句时） -->

  <!-- 4. 前言正文（开场白，组件5 段落 × N） -->

  <!-- 5. 第一章（组件4 chapter-title，margin-top:16px） -->
  <!--    章内：组件5 正文 + 组件6 行内样式 + 组件7 标签 + 组件8 代码 + 组件9 引用亮点 + 组件10 提示 + 组件11 布局 + 组件12 媒体 -->

  <!-- 6. 第二章…第N章（组件4，margin-top:48px） -->

  <!-- 7. 结语章（组件4 变体：编号 ///，PART 改 LAST，章名"写在最后"） -->

  <!-- 8. 作者签名（组件5 段落，放在 footer-cta 前） -->

  <!-- 9. 互动三连（组件13a footer-cta） -->

  <!-- 10. 品牌尾图（组件13b，有素材才加） -->

</section>
```

---

## 视觉层级（3 层递进）

| 层级 | 样式 | 用途 | 频率 |
|------|------|------|------|
| **锚点层** | 蓝色加粗 6a / 橙色亮点卡 9b | 核心概念、产品名、关键结论 | 全文 ≤5 处 |
| **标记层** | 蓝色下划线 6e（默认）/ 橙色渐变高亮 6c | 正文关键词强调 | 每段 1~3 处 |
| **容器层** | 蓝色竖条引用 9a / 提示 10x / 胶囊 11a | 引用、旁注、提示 | 按需 |

**克制原则**：
- 橙色高亮每段 ≤1-2 处
- 蓝色加粗全文 ≤5 处
- 蓝色下划线是正文关键词默认标记
- 红色下划线只用于对比/否定

---

## 文章类型 → 组件组合配方

| 文章类型 | 核心组件组合 | 点缀组件 |
|----------|------------|---------|
| 教程/操作指南 | step-label 7a + cmd/prompt 8a/8b + 代码块（通用库1a） | warn-tip 10a、blue-tip 10b |
| 盘点/工具清单 | skill/tool-label 7c + pill-list 11a | table 11c、oneliner-card 9b |
| 观点/深度分析 | paragraph 5 + quote-box 9a + oneliner-card 9b | center-divider 9d、subtitle-highlight 9c |
| 访谈/人物特稿 | paragraph 5 + quote-box 9a + ordered-list 11b | oneliner-card 9b、center-divider 9d |
| 数据复盘/报告 | table 11c + ordered-list 11b | blue-info 10d、橙色高亮 6c |
| 生活/情感随笔 | paragraph 5 + oneliner-card 9b + center-divider 9d | quote-box 9a（少量） |
| 案例实战 | case-label 7b + step-label 7a | prompt-block 8a、orange-warning 10c |

所有类型共用固定结构：封面 2 + 目录 3 + 章节标题 4 + 签名/三连 13。

---

## Markdown → 蓝橙简约排版 映射规则

| Markdown 元素 | 对应组件 | 说明 |
|---|---|---|
| `# 标题` | 不使用 | 公众号文章标题在平台设置 |
| 文章开头 `> 引言` | 组件 9b oneliner-card | 开头金句 |
| `## 章节标题` | 组件 4 chapter-title | PART 01/02/03…，末章 /// + LAST |
| `### 子标题` | 组件 9c subtitle-highlight | 橙色底划线小节标题 |
| 普通段落 | 组件 5 paragraph | 每段标 1~3 处蓝色下划线 6e |
| `**加粗文字**` | 组件 6a 蓝色加粗 | 核心概念/品牌名 |
| `==高亮文字==` | 组件 6c 橙色渐变高亮 | 每段 ≤2 处 |
| `<u>下划线</u>` / `++文字++` | 组件 6e 蓝色下划线 | 次要强调 |
| `~~删除线~~` | 组件 6i 删除线灰色 | 被淘汰的概念 |
| `> 引用段落`（非开头） | 组件 9a quote-box | 蓝色竖条引用 |
| 核心金句 | 组件 9b oneliner-card / 9d center-divider | 视觉焦点 |
| 操作步骤 | 组件 7a step-label | STEP 01/02… |
| 案例/场景 | 组件 7b case-label | CASE 01/02… |
| 技能/工具清单 | 组件 7c skill/tool-label | 蓝色标签 |
| Prompt 提示词 | 组件 8a prompt-block（短）/ 通用库 1a（长多行） | |
| 单行命令 | 组件 8b cmd-block | |
| 多行代码块 | 通用库 1a 深色（默认）/ 1b 浅色（左竖条换 #2563EB） | |
| 行内代码 | 组件 6g 代码标签 | |
| 并列要点 | 组件 11a pill-list | 蓝色胶囊 |
| Markdown 表格 | 组件 11c table | 蓝色表头，偶数行暖灰底 |
| `1. 2. 3.` 编号列表 | 组件 11b ordered-list | 蓝色/橙色方块数字 |
| 注意/警告 | 组件 10a warn-tip / 10c orange-warning | |
| 亮点提示 | 组件 10b blue-tip / 10d blue-info | |
| `![](图片)` | 组件 12a image | 原图代码保留 |
| `![](xxx.gif)` | 组件 12b GIF 动图 | 加动图角标 |
| 文末 | 组件 13a footer-cta（+ 13b brand-card） | 签名段落放 footer-cta 前 |
