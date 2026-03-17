# Chainspeak

A conversation-first language learning project for Korean and Mandarin Chinese.

The core idea: fluency comes from having something to say, not from memorizing grammar tables. This project focuses on a 7-week arc of chained conversation drills — 18 reps total — that follow a single storyline from meeting a stranger to making plans with a friend. Each rep feeds into the next. Each week picks up where the last one ended.

The content is pitched at beginners — someone who can produce a few words but hasn't yet learned how to hold a conversation. That said, the structure itself isn't beginner-only. Intermediate and advanced learners can swap in more complex vocabulary, extend the beat prompts, or build entirely new weeks around topics that match where they are.

A single HTML file that opens in a browser.

---

## 🫖 Origin: Tony Marsh's 1·2·3 Cups Method

Chainspeak grew out of Tony Marsh's **1·2·3 Cups** method — a conversation-first approach developed over 15 years of language instruction for the US Military, FBI, and NATO. The original method uses three nested cups per verb:

1. A statement (Cup 1)
2. A yes/no question (Cup 2)
3. An open question (Cup 3)

The answer to the open question seeds the next set of cups. You're not drilling isolated sentences — you're generating vocabulary from the natural flow of a real exchange.

Chainspeak takes that logic and extends it into a full conversational arc. The cup structure lives on in the Verb Seeds tab. The chaining principle runs through every rep in the weekly drills.

---

## 🥁 The 4-Beat Method

Every rep in chainspeak follows the same 4-beat cycle:

```
STMT → ASK → ECHO → BRIDGE
```

| Beat | What you do | Why |
|------|-------------|-----|
| **STMT** | Make a statement — share something real | Puts information on the table |
| **ASK** | Ask an open question on the same topic | Invites the other person in |
| **ECHO** | Confirm what you heard | Shows you were listening; buys thinking time |
| **BRIDGE** | React, then pivot to the next topic | Keeps the conversation moving forward |

The BRIDGE beat is the key one. Every rep ends with a line that goes somewhere — into the next rep, the next week, or back to something said earlier in the arc. The goal isn't isolated sentence production; it's keeping a conversation going without stalling.

#### Example (Week 1, Rep 1 — Origin)

> **STMT** — 저는 뉴욕에서 왔어요. / 我是纽约人。  
> **ASK** — 어디에서 왔어요? / 你是哪里人？  
> **ECHO** — (partner says 부산/成都) → 부산에서요? / 成都人？  
> **BRIDGE** — 좋은 데! 지금도 부산에서 살아요? / 听说那边的火锅特别好吃！你现在还住在成都吗？

The bridge question — *do you still live there?* — opens Rep 2 (Residence). The conversation doesn't stop; it continues.

---

## 🌱 The Verb Seeds Reference

The **Verb Seeds** tab is a conjugation reference for 12 core verbs across 3 tenses — Present, Past, and Future — in both Korean and Mandarin.

**The 12 verbs:**

| Korean | Chinese | English |
|--------|---------|---------|
| 이다 | 是 | to be |
| 있다 | 有 | to have |
| 가다 | 去 | to go |
| 하다 | 做 | to do |
| 오다 | 来 | to come |
| 원하다 | 想 | to want |
| 좋아하다 | 喜欢 | to like |
| 먹다 | 吃 | to eat |
| 보다 | 看 | to see |
| 알다 | 知道 | to know |
| 말하다 | 说 | to say / speak |
| 살다 | 住 | to live |

Each verb entry includes:
- **8 swappable vocabulary words** — drop any of them into the cup structures below
- **S / Y/N / Q cup structure** for the selected tense — the 1·2·3 Cups pattern: statement, yes/no question, open question
- **Short grammar notes** for Korean and Chinese — kept separate so you can read one language at a time without the other getting in the way; they're there to flag the one or two things that actually trip people up with that verb, not to explain the whole grammar system

This tab is a reference to come back to, not a drill. When a verb from the weekly drills needs more context, pull this up and work through the tenses.

---

## ⛓️ The 7-Week Arc

```
Week 1 — Meeting Someone    Origin → Residence → Work
Week 2 — Hobbies            General interests → Going deeper → Trying new things
Week 3 — Food               Restaurant recs → Food preferences → Making plans
Week 4 — Travel             Travel dreams → Past experiences → If I went there...
Week 5 — Goals              Life goals → Motivation → Challenges
Week 6 — Feelings           How are you really? → Self-care → Full circle
Week 7 — Full Review        Chain all 18 reps from memory
```

The arc closes on itself. A dinner plan made in Week 3 gets referenced in Week 6. Week 7 has no new content — just a full recall of the entire arc as one continuous conversation.

---

## Getting Started

1. Download `chainspeak.html`
2. Open it in any modern browser
3. Use the language toggle — **한국어** (Korean only), **Both** (side by side), **中文** (Mandarin only)
4. Work through weeks in order — each Bridge assumes you've done the previous week
5. In each rep: say every beat out loud before expanding the reference conversation
6. On Week 7: chain all 18 reps from memory with the references closed

---

## Extending the Project

All content lives in plain JavaScript objects inside a single `<script>` tag. No build step. Edit the file directly.

### Adding a Beat

Use the `B()` helper:

```js
B(
  "b1",                          // beat type: b1=STMT, b2=ASK, b3=ECHO, b4=BRIDGE
  "STMT",                        // label shown on the colored tag
  "Prompt text for the learner.",
  "grammar or vocab hint",
  "target sentence structure",   // optional
  "partner response",            // optional — renders as a speech bubble
  "pinyin for partner response"  // optional — Mandarin only
)
```

### Adding a Rep

Use the `makeRep()` factory:

```js
makeRep(
  1,                    // rep number (1, 2, or 3)
  "Rep Title",
  "verb · 动词 eng",   // displayed as a pill badge in the rep header
  "Scenario text — sets the scene in italics.",
  {                     // Korean content
    beats: [ B(...), B(...), B(...), B(...) ],
    ref:   [ {who:"you", text:"..."}, {who:"partner", text:"..."}, ... ],
    vocab: [ {w:"word", m:"meaning"}, ... ]
  },
  {                     // Mandarin content — same shape, add py: field for pinyin
    beats: [ B(...), B(...), B(...), B(...) ],
    ref:   [ {who:"you", text:"...", py:"..."}, ... ],
    vocab: [ {w:"word 拼音 pīnyīn", m:"meaning"}, ... ]
  }
)
```

### Adding a Week

Add an entry to the `weeks` array:

```js
{
  title: "Your Topic",
  task: "Instruction shown in the task bar.",
  isReview: false,
  reps: [ makeRep(...), makeRep(...), makeRep(...) ],
  bridges: {
    kr: [ {p:"pattern", m:"meaning"}, ... ],
    zh: [ {p:"pattern pīnyīn", m:"meaning"}, ... ]
  }
}
```

The week selector builds itself from the `weeks` array — no HTML changes needed.

### Adding a Verb Seed

1. Add a key to the `verbs` object following the existing structure
2. Add the key to `verbOrder`

The verb buttons build themselves dynamically — no HTML changes needed.

---

## Language Notes

| | Korean | Mandarin |
|--|--------|---------|
| Register | 해요체 (informal polite) | Standard Mandarin (普通话) |
| Script | Hangul only — no romanization | Simplified characters |
| Pinyin | Not shown in drills | Reference conversations only |
| Tones | Not drilled — supplement with immersion listening | — |

---

## Stack

Vanilla JavaScript. Google Fonts (Noto Serif KR, Noto Serif SC, Playfair Display). Single HTML file.

---

## Credits

Built on Tony Marsh's 1·2·3 Cups method. Structured for Korean (해요체) and Mandarin Chinese (普通话).
