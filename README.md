# TCM Wellness Advisor · 华佗在线

> A WorkBuddy / Claude-style agent skill that turns plain-language symptom descriptions into TCM constitutional assessment and practical wellness guidance — food remedies, acupressure, and daily routines — with hard safety boundaries.

**中文简介**：把用户的身体描述转换为中医体质判断，并给出食疗、穴位、作息的日常调理建议。内置安全边界：严重症状一律建议就医，不诊断疾病。→ [中文说明](#中文说明)

---

## Why this exists

Most "AI health" tools either over-claim (pretending to diagnose) or under-deliver ("rest more, eat light"). This skill takes a middle path that TCM actually supports well: **pattern-based wellness guidance** — identify a constitutional tendency, then give concrete, cookable, doable advice.

## Features

- **Nine-constitution assessment** — qi deficiency, yang deficiency, yin deficiency, phlegm-damp, damp-heat, blood stasis, qi stagnation, special/allergic constitution, balanced. Handles compound constitutions and their conflicting advice.
- **Food remedies with format variety** — porridge, soup, cooked dishes, compotes/desserts, teas. Never a wall of tea recipes.
- **Acupressure** — safe, easy-to-locate points in everyday measurements, with pregnancy contraindications.
- **Four-diagnostics workflow** — structured inquiry checklist, tongue-photo reading (multimodal), honest limits on pulse diagnosis.
- **Classical citations, no fabrication** — a curated quotation library plus optional full-text corpus retrieval; fabricated classical quotes are explicitly forbidden by the skill's own rules.
- **Hard safety boundaries** — red-flag symptoms, persistent conditions, pregnancy/children/chronic disease, and unsafe herbs all route to medical care instead of wellness advice.

## Install

```bash
# 1. Download or clone this repo
git clone https://github.com/<your-name>/tcm-wellness-advisor.git

# 2. Copy into your skills directory
#    user-level (all projects):
cp -r tcm-wellness-advisor ~/.workbuddy/skills/
#    or project-level (shared with a repo's collaborators):
cp -r tcm-wellness-advisor <project>/.workbuddy/skills/

# 3. Start a new session — the skill loads automatically
```

On Windows the user-level path is `C:\Users\<you>\.workbuddy\skills\`.

## Usage

Just describe the problem in everyday language:

| You say | What happens |
|---------|--------------|
| "I'm always exhausted, no energy even after sleeping" | Qi-deficiency tendency → food remedies, Zusanli acupressure, sleep adjustments |
| "My hands and feet are always cold" | Yang-deficiency tendency → warming recipes, daily sun exposure plan |
| "I break out and feel bitter-mouthed after late nights" | Damp-heat tendency → clearing recipes, routine reset |
| "What's my body type?" | Structured inquiry, then assessment |
| "What do the classics say about insomnia?" | Symptom → historical disease name → full-text retrieval (full edition) |

Works in Chinese and English prompts; the knowledge base itself is written in Chinese (TCM terminology is most precise in the source language).

## Repository structure

```
tcm-wellness-advisor/
├── SKILL.md                    # workflow, safety boundaries, output format
└── references/
    ├── constitutions.md        # nine body types + follow-up questions
    ├── diet-therapy.md         # recipes by pattern, format requirements
    ├── acupoints.md            # safe points, contraindications
    ├── routine.md              # sleep / exercise / seasonal routines
    ├── classics.md             # curated classical quotes + citation rules
    ├── four-diagnostics.md     # inquiry checklist, tongue reading
    └── disease-map.md          # modern symptom → historical disease names
```

## Lite vs. full edition

This repository is the **lite edition** (~25 KB): everything except the classical full-text corpus. The **full edition** adds `references/texts/` — 700 classical Chinese medical texts (~164 MB) for offline full-text citation retrieval. Build it yourself by downloading any public-domain TCM text corpus (e.g. the open-source 殆知阁 collection) into `references/texts/`; the retrieval workflow in `SKILL.md` picks it up automatically.

## Safety & compliance

This project is **wellness education, not medical care**. It deliberately refuses to:

- diagnose disease or interpret lab results,
- recommend toxic or unprescribed herbs,
- give wellness advice for red-flag symptoms.

Every answer carries a disclaimer. If you deploy this commercially (e.g. as a mini-program or app), note that regulated jurisdictions restrict medical claims — keep it positioned as general wellness information, avoid treatment/efficacy claims, and consult local regulations (in China: 互联网诊疗监管 and 广告法 apply).

## Data & attribution

- Classical quotations are from public-domain Chinese medical classics (《黄帝内经》《伤寒论》《金匮要略》, etc.).
- The full-edition corpus source referenced is the open-source 殆知阁古代文献 (daizhigev20) collection; attribution is retained in `references/classics.md`.
- Recipes and point locations are compiled from common TCM wellness literature and are intended as everyday reference.

## License

MIT — see [LICENSE](LICENSE). Content is provided as-is, without warranty of any kind.

---

## 中文说明

**华佗在线** 是一个 WorkBuddy 技能：根据你描述的身体状况判断中医体质倾向，给出**食疗、穴位按摩、作息起居**三方面的具体建议，并可引用中医古籍原文（有严格的反编造规则）。

**安装**：把本目录复制到 `~/.workbuddy/skills/` 下，重开会话即可生效。

**特色**：

- 九种体质辨识，支持复合体质
- 食疗方覆盖粥/汤/菜/羹/茶多种形式，不是只会让你喝茶
- 支持上传舌照辅助判断（望诊），并如实声明脉诊需线下进行
- 内置安全边界：红旗症状（胸痛、高热等）、孕妇儿童慢性病患者、有毒中药一律不推荐，直接建议就医
- 古籍引用只引收录或核实内容，禁止编造原文

**轻量版 vs 完整版**：本仓库是轻量版（约 25KB），不含 700 部古籍全文语料库（完整版约 61MB）。需要古籍全文检索能力时，把公版中医古籍语料下载到 `references/texts/` 即可自动启用检索流程。

**声明**：本项目仅供养生科普参考，不构成医疗建议，不诊断疾病。商业部署前请确认当地法规（国内需注意互联网诊疗监管与广告法对疗效宣传的限制）。
