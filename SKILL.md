---
name: figma-prd-annotation
description: 基于最终 PRD 为 Figma 设计稿生成规范、美观、可评审的产品与交互标注。Use when the user provides a final PRD and a Figma design link or asks to annotate, mark up, document, review, label, or prepare a Figma design for product/design/engineering handoff according to PRD rules, interaction states, metrics, permissions, or edge cases.
---

# Figma PRD Annotation

## Overview

Use this skill to transform a final PRD into concise, polished Figma annotations. The goal is to make the design file easier to review, align, and hand off without creating reading friction or turning the canvas into another PRD.

Default to Chinese output. When the user provides a Figma design link and asks to view, modify, annotate, screenshot, organize, or optimize the design, use Figma MCP / `figma-use` directly if available. Do not ask whether to use Figma tools unless the user explicitly says not to modify Figma, not to use tools, or only wants text in chat.

## Required Inputs

- Final or near-final PRD.
- Figma file/node link.
- Optional: target frame/page, audience of the annotation, and whether annotation is for product review, design review, or engineering handoff.

If the PRD is incomplete, annotate only confirmed rules and create a visible "待确认" annotation group for unresolved questions.

## Workflow

1. **Read the PRD first**
   - Extract product goal, target users, scenarios, module list, flow, interaction rules, states, data fields, permissions, metrics, risks, and open questions.
   - Separate confirmed PRD content from inferred interpretation.
   - If needed, use `$prd-design-audit` first to produce a design overview before annotating.

2. **Read the Figma target**
   - Use Figma MCP tools to read node structure and screenshot.
   - Identify target frames, components, repeated modules, variants, and visible interaction states.
   - If Figma tools are unavailable or permission is not connected, state that clearly and provide a text-only annotation plan instead.

3. **Create an annotation map**
   - Match PRD requirements to visible Figma nodes.
   - Use `references/annotation-system.md` for annotation categories, naming, color, and layout rules.
   - Prioritize only annotations that reduce ambiguity for PM, design, engineering, data, QA, ops, or legal/compliance.
   - Avoid annotating obvious static UI, repeated rules, or content that is already self-evident from the screen.
   - Prefer a small number of high-signal annotations over complete coverage.

4. **Modify Figma**
   - Add a dedicated annotation layer/page/section near the target frame.
   - Use consistent compact callout components, numbering, color tags, and connector lines.
   - Place annotations outside the main design whenever possible. Do not cover key UI content.
   - Group annotations by frame/module and name layers clearly.
   - Preserve the original design; do not alter product UI unless the user asks for design changes.

5. **Verify with screenshots**
   - Capture the annotated design after modification.
   - Check readability, overlap, connector accuracy, visual hierarchy, and whether annotations correspond to PRD rules.
   - Revise if labels are crowded, ambiguous, too small, or visually messy.

6. **Deliver**
   - Provide the Figma link, preview screenshot if available, concise change summary, and unresolved PRD questions.
   - Include an annotation index when the file has many notes.

## Annotation Types

Use four compact types by default:

- **规则**: key behavior, permission, data, metric, or business rule that affects implementation.
- **状态**: important non-happy-path state such as empty, loading, error, disabled, pending, rejected, expired, or no permission.
- **异常**: failure, fallback, recovery, risk, or compliance case that changes the experience.
- **待确认**: PRD ambiguity or missing rule that blocks confident handoff.

Only create a separate detailed index when the user explicitly asks for engineering-grade handoff or the flow is too complex for compact callouts.

## Output Format

Use this structure in the final response:

```markdown
已完成 Figma 标注。

- Figma 链接：
- 预览图：
- 标注范围：
- 新增标注：
- 待确认问题：
```

For text-only plans, use:

```markdown
## 标注方案
| 编号 | 类型 | 对应模块 | 标注内容 | PRD 依据 | 状态 |
|---|---|---|---|---|---|
```

## Quality Bar

- Annotations must be useful for handoff, not decorative.
- PRD uncertainty must be labeled as uncertainty.
- Keep annotation language short, concrete, and implementation-friendly. Default to one sentence per annotation.
- Keep the canvas lightweight: annotate critical decisions, not every requirement.
- Use consistent visual style; do not create a messy collection of one-off text boxes.
- Verify the final screenshot before claiming completion.
- Do not repeatedly ask whether to use Figma tools when the user has already provided a Figma link and requested annotation.

## References

- Read `references/annotation-system.md` before creating annotation content or modifying Figma.
