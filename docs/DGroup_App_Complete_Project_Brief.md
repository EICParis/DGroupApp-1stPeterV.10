# Rueil D-Groups Bible Study App: Complete Project Brief

## Who We Are

This app is being developed by the pastoral team at Emmanuel International Church (EIC), located in Rueil-Malmaison, France. The lead developer and content author is Christian Nartatez, a Venezuelan pastor and preacher who teaches in English. The app is designed to serve the church's discipleship groups (D-Groups), small groups of believers who meet regularly to study the Bible together.

## Mission

To give new believers and growing disciples a practical, interactive tool for studying the Bible in depth. The app walks the user through a structured method of reading Scripture: starting with the text itself, understanding its context, identifying repeated themes, exploring definitions, seeing visual resources, and reading pastoral commentary. Everything is built to help people read the Bible for themselves, not just hear someone else's opinion about it.

## Vision

A single-page web application that feels like sitting down with a pastor who opens the Bible and says: "Let me show you what's really happening here." The app should be warm, clear, and accessible to someone who has never opened a Bible before, while still being rich enough to reward someone who has studied it for years. The first book available is 1 Peter (5 chapters, WEB translation). The architecture is designed so that additional books can be added later by loading new JSON files.

## Design Philosophy

The design is clean, elegant, and intentional. It avoids anything that looks like a generic AI-generated interface. The visual identity comes from Emmanuel International Church's branding.

### Brand Colors (Light Mode)

| Name | Hex | Usage |
|------|-----|-------|
| Gris Light | #F3F4F4 | Page background |
| Red | #9B1B34 | Primary accent, highlights, selected verse, header bar |
| Dark Gray | #3A3A3C | Main body text |
| Light Pink | #F9F3F5 | Soft backgrounds, hover states, highlighted areas |
| Mid Gray | #808285 | Secondary text, labels, captions |
| White | #FFFFFF | Cards, content panels, inputs |

### Dark Mode

The app supports a dark mode toggle. Dark mode uses deep grays and near-blacks with the same red accent (#9B1B34) carried through. All PNG images have both a light and a dark version. Image filenames follow this convention:

- `image_name_light.png` for light mode
- `image_name_dark.png` for dark mode

The app switches between them based on the current mode.

### Typography

The only font used across the entire app is **Roboto** (Google Fonts). No other font families. Weights used: 300 (light), 400 (regular), 500 (medium), 700 (bold), 900 (black for special headers). All text throughout the app, including titles, labels, body text, pills, buttons, and captions, uses Roboto exclusively.

### Writing Style

All text content is written by Christian in his authentic voice as a preacher teaching in English. The language is simple, direct, and accessible to new believers. There are no em dashes anywhere in the project. All content uses periods, commas, and natural sentence restructuring instead. This is a strict rule across all files: JSON, markdown, and in-app text.

## App Structure: 5 Interactive Steps on One Page

The app is a single scrollable page with 5 vertically stacked sections. The user selects a Chapter and Verse at the top, and all sections below update accordingly.

### Header

- Left: App logo (red circle with stylized "d" letter)
- Center: "D-Groups Bible Study App" with subtitle "1st Peter WEB, Bible Version"
- Right: Emmanuel International Church logo
- Dark mode toggle button

### Prayer Banner

A subtle banner below the header that reads: "Start your bible study by praying as you ask God for direction..."

### Select Passage (Chapter + Verse)

Two dropdown selectors for Chapter (1 through 5) and Verse (dynamic based on chapter). When the user changes the selection, all 5 steps below update.

### Step 1: Context View

Displays the selected verse highlighted in the center, with 3 verses before and 3 verses after from the same chapter. The selected verse appears in red/bold with a left border accent. Surrounding verses gradually decrease in opacity and size to create a visual focus effect.

Includes an expandable "Why Does Context Matter?" section with this explanation:

"Every verse in the Bible lives inside a conversation. When you pull a verse out of that conversation, you risk changing what it actually means. Think of it like walking into a room where two people are talking and you only hear one sentence. You might think they're arguing when they're actually joking. You might think they're sad when they're actually celebrating. That one sentence only makes sense when you hear what came before it and what comes after it. This section shows you the verses that surround the one you selected. The verse you're studying appears highlighted in the center, and you can see what Peter was saying right before and right after. This way, you're not reading a sentence in isolation. You're reading it inside the flow of Peter's thought, which protects you from giving it a meaning that Peter never intended. Read the context first. Then study the verse. That's how you let the Bible speak for itself."

### Step 2: Repeated Words

Three tabs: "Key Words (Concepts)", "Action Verbs", and "Pronouns". Each tab shows clickable word pills/bubbles displaying the word and its frequency count for the current chapter. The size of each pill scales proportionally to the word's frequency. Clicking a keyword opens its glossary entry in Step 3.

Includes an expandable "The Insight in Repetition" section.

### Step 3: Glossary of Terms

When the user clicks a keyword in Step 2, this section appears showing:

1. **The word** in large text
2. **Definition** written in simple language for new believers
3. **Key Verse** from 1 Peter with the reference
4. **Total appearances** across the entire letter
5. **Category** the word belongs to, with the category image, name, and description

The 52 keywords are organized into 4 global categories, each named from Peter's own words:

| Category | Image Tag | Words | Source |
|----------|-----------|-------|--------|
| The Living God | living_god | 12 words (God, Christ, Jesus, Spirit, Lord, Father, Glory, Power, Holy, Word, Revelation, Amen) | 1 Peter 1:3 |
| The Precious Blood | precious_blood | 13 words (Grace, Mercy, Salvation, Blood, Resurrection, Precious, Stone, Cornerstone, Incorruptible, Heaven, Forever, Peace, Gold) | 1 Peter 1:19 |
| The Royal Priesthood | royal_priesthood | 15 words (Good, Faith, Souls, People, Priesthood, Foreigners, Flock, Brothers, Spiritual, Obedience, Conscience, Humility, Righteous, Shepherd, Will) | 1 Peter 2:9 |
| The Fiery Trial | fiery_trial | 12 words (Evil, Flesh, Sufferings, Life, Sins, Dead, Sin, Suffering, Disobedient, World, Grass, Flower) | 1 Peter 4:12 |

Each category has its own header image (light and dark versions) and a description paragraph.

### Step 4: Visual Overview by Chapter

Displays a static PNG image relevant to the selected chapter. For 1 Peter, these are hand-designed illustrations or maps (for example, Chapter 1 might show a map of Asia Minor with Peter's audience regions). Each chapter has its own image, with light and dark versions.

### Step 5: Commentary by Chapter

Displays pastoral commentary for the selected chapter, organized into expandable sections. The commentary is written by the pastoral team at EIC and loaded from a JSON file. Each chapter's commentary is broken into titled sections that the user can click to expand and read.

Includes an "About This Commentary" disclaimer at the bottom explaining that the content comes from the pastoral team and that AI was used only as an editorial tool for cleanup and translation, not for generating theological content.

### Footer

- "Apply today's lesson to your daily walk."
- "Remember to close in prayer."
- App name, church name, copyright notice

## Data Architecture

All content is driven by external JSON files. Nothing is hardcoded in the UI.

### Files Ready

| File | Description | Status |
|------|-------------|--------|
| `1peter_web.json` | Full Bible text for 1 Peter, organized by chapter and verse (WEB translation) | Ready |
| `repeated-words.json` | Word frequency analysis for all of 1 Peter, with 52 keywords, 38 action verbs, and 24 pronouns. Each word includes total count and per-chapter breakdown. | Ready |
| `1peter_glossary.json` | Glossary of 52 keywords with definitions, key verses, references, total counts, and category tags (category_key, category_label, image_tag). Also includes the 4 category descriptions. | Ready |
| Commentary JSON | Chapter-by-chapter pastoral commentary in expandable sections | Pending (converting from Word documents) |

### Image Assets Expected

| Image | Versions | Naming Convention |
|-------|----------|-------------------|
| App logo (red "d" circle) | Light + Dark | `logo_d_light.png`, `logo_d_dark.png` |
| Emmanuel Church logo | Light + Dark | `logo_emmanuel_light.png`, `logo_emmanuel_dark.png` |
| Chapter illustrations (5) | Light + Dark | `chapter_1_light.png`, `chapter_1_dark.png`, etc. |
| Category headers (4) | Light + Dark | `living_god_light.png`, `living_god_dark.png`, etc. |

## Tech Stack

- **Framework:** React (single-page application)
- **Font:** Roboto (Google Fonts), exclusive
- **Data format:** JSON
- **Hosting target:** Lovable.dev or Vercel (to be decided)
- **Future features:** User accounts, saved notes, group sharing, multi-language support, additional Bible books

## Visual Reference

The complete visual mockup of the app layout is available in these files:

- `DGroupBibleApp-Structure2026.png` (full-length mockup showing all 5 steps)
- `DGroupBibleApp-Structure2026.pdf` (same mockup in PDF with readable text)
- `DGroupAppBibleStudyGraphic.png` (original 6-layer architecture diagram)

These files should be used as the primary visual reference for layout, spacing, typography hierarchy, and interaction patterns. The mockup shows the exact arrangement of every section, including the prayer banner, select passage area, context view, repeated words with pill layout, glossary with category cards, visual overview placeholder, commentary with expandable sections, and footer.

## Key Rules for Any AI Working on This Project

1. **Only use Roboto.** No other fonts, ever.
2. **Never use em dashes.** Use periods, commas, or restructure the sentence.
3. **All colors must match the brand palette.** Red #9B1B34 is the accent in both light and dark mode.
4. **All content must be simple enough for a new believer to understand.** No complex theological jargon.
5. **All content is written in Christian's voice as a preacher.** Direct, warm, practical, with vivid illustrations.
6. **The app is data-driven.** All text, words, definitions, and commentary come from JSON files, not from hardcoded strings.
7. **Dark mode requires separate image assets.** Use the image_tag field plus "_light" or "_dark" suffix to load the correct version.
8. **The Bible version is WEB (World English Bible).** Do not substitute with any other translation.
9. **The visual mockup is the authority for layout decisions.** When in doubt, match the mockup.
10. **The 52 keywords and their 4 categories are final.** Do not add, remove, or recategorize words without explicit instruction from Christian.
